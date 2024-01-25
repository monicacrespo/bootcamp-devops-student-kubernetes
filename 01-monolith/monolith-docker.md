# Monolith using Docker

1. [How to run the monolith with Docker](#docker)
2. [Cleaning Up](#cleaning)

<a name="docker"></a>
## 1. How to run the monolith with Docker

Please follow these steps:
1. Create the network
   ```bash
   cd ./01-monolith/todo-app
   docker network create monolith-network
   ```
2. Start up a database to work locally. To create the container for postgres run the following command:
   ```bash
   docker run -d --network monolith-network -p 5432:5432 -v todos:/var/lib/postgresql/data --name postgres postgres:10.4
   ```

   Once the container is running, if the database was not initialized, populate the data by running the following commands:

   ```bash
    docker exec -i postgres psql -U postgres < todos_db.sql
   ```
   Notice that since we have a volume we will not need to run again the above code.

3. Create .env with
    ```env
    NODE_ENV=production
    PORT=3001
    DB_HOST=localhost
    DB_USER=postgres
    DB_PASSWORD=postgres
    DB_PORT=5432
    DB_NAME=todos_db    
    DB_VERSION=10.4
    ```
4. Run the client application. 
   * For that first we need to create the image of our todo-app
      ```bash
      $ docker build -t binarylavender/todo-app-monolith:v1 . 
      ```

   * Then, push to Docker Hub (Registry configured by default)
      `docker push binarylavender/todo-app-monolith:v1`

   * Create the container 
      ```bash
         docker run -d --network monolith-network -p 3001:3001 \
         -e NODE_ENV=production \
         -e PORT=3001 \
         -e DB_HOST=postgres \
         -e DB_USER=postgres \
         -e DB_PASSWORD=postgres \
         -e DB_PORT=5432 \
         -e DB_NAME=todos_db \
         -e DB_VERSION=10.4 \
         --name todo-app-monolith \
         binarylavender/todo-app-monolith:v1
      ```
<a name="cleaning"></a>
## 2. Cleaning Up

      ```bash
      docker network rm monolith-network
      ```
