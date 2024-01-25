# Monolith using Docker

1. [Data persistence layer using Official Postgres image](#persistence)
2. [Postgres Official Image](#official)

<a name="persistence"></a>
## 1. Data persistence layer using Official Postgres image

Another approach to create a data persistence layer without using a custom image is to put the SQL file in a ConfigMap, and then mount it inside the container at the appropriate location. The advantage to doing this is that you can upgrade/downgrade the postgres image by simply changing the Deployment manifest; you don't need to build a new image.


Kustomization file that creates a ConfigMap called `postgres-init-config` from the `config/todos_db.sql` file.

```yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
commonLabels:
   app: postgres
resources:
- postgres-storageclass.yaml
- postgres-persistentvolume.yaml
- postgres-persistentvolumeclaim.yaml
- postgres-service.yaml
- postgres-statefulset.yaml

configMapGenerator:
   - name: postgres-cm
   envs:
   - config/postgres.env
   - name: postgres-init-config
   files:
   - config/todos_db.sql

generatorOptions:
   disableNameSuffixHash: true # use a static name  
```
The below configmap is the generated ConfigMap manifest.

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
   labels:
   app: postgres
   name: postgres-init-config
data:
   todos_db.sql: "--\r\n-- PostgreSQL database dump\r\n--\r\n\r\n-- Dumped from database
   version 10.4 (Debian 10.4-2.pgdg90+1)\r\n-- Dumped by pg_dump version 10.4 (Debian
   10.4-2.pgdg90+1)\r\n\r\nSET statement_timeout = 0;
   ...
   "
```

```yaml
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: postgres
spec:  
  selector:
    matchLabels:
      app: postgres     
  serviceName: postgres
  replicas: 1
  template:
    metadata:
      labels:
        app: postgres
      spec:
        containers:
        - name: postgres
          image: postgres:10.4
          envFrom:
          - configMapRef:
              name: postgres-cm
          ports:
          - containerPort: 5432
            name: postgres
          volumeMounts:
          - mountPath: /docker-entrypoint-initdb.d
            name: postgres-init-config
          - name: todos     
            mountPath: /var/lib/postgresql/data
          resources:
            requests:
              cpu: 250m
              memory: 256Mi
        volumes: 
        - configMap:
            name: postgres-init-config
          name: postgres-init-config
  volumeClaimTemplates:
  - metadata:
      name: todos
    spec:
      storageClassName: standard
      accessModes:
      - ReadWriteOnce
      resources:
        requests:
          storage: "512Mi"
```

<a name="official"></a>
## 2. Postgres Official Image

You can find the information about postgres Official Image [here](https://hub.docker.com/_/postgres). The key points are: 
* POSTGRES_PASSWORD. This environment variable is required for you to use the PostgreSQL image. 
* POSTGRES_USER. This optional environment variable is used in conjunction with POSTGRES_PASSWORD to set a user and its password. This variable will create the specified user with superuser power and a database with the same name. If it is not specified, then the default user of `postgres` will be used.
* POSTGRES_DB. This optional environment variable can be used to define a different name for the default database that is created when the image is first started. If it is not specified, then the value of POSTGRES_USER will be used.
