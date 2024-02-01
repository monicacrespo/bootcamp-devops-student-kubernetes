# DevOps - Lemoncode - Kubernetes Exercises
1. [Introduction](#intro)

<a name="intro"></a>
## 1. Introduction

We've been asked by LemonCode team to implement the solution of these three exercises:
* Exercise 00. Monolith in memory
    * This is a web app that exposes an UI app (the typical to-do list app), and an API to manage in the server the 'TODOS'. 

    * The TODOS persistency is in-memory, which means that the data is lost when app is closed. 
  
    * You can see what's need to be done in this exercise in [exercise monolith in memory](https://github.com/Lemoncode/bootcamp-devops-lemoncode/blob/master/02-orquestacion/exercises/00-monolith-in-mem/exercise-monolith-in-memory.md).

    * To build the image of this app, look at the steps provided by LemonCode in [00-monolith-in-mem/README.md](https://github.com/Lemoncode/bootcamp-devops-lemoncode/blob/master/02-orquestacion/exercises/00-monolith-in-mem/README.md).

* Exercise 01. Monolith
    * Same app but in this case, the in-memory persistency is done through a database.

    * You can see what's need to be done in this exercise in [exercise monolith](https://github.com/Lemoncode/bootcamp-devops-lemoncode/blob/master/02-orquestacion/exercises/01-monolith/exercise-monolith.md).

    * To run the app locally and with docker you can follow the steps in [monolith-docker.md](https://github.com/monicacrespo/bootcamp-devops-student-kubernetes/blob/main/01-monolith/monolith-docker.md).

* Exercise 02. Distributed Application
    * There are two apps, one UI exposed via an nginx and one express/nodejs API that connects to a postgres database.

    * You can see what's need to be done in this exercise in [exercise-ingress](https://github.com/Lemoncode/bootcamp-devops-lemoncode/blob/master/02-orquestacion/exercises/02-distributed/exercise-ingress.md).

    * To run the app locally and with Docker you can follow the steps in [distributed-docker.md](https://github.com/monicacrespo/bootcamp-devops-student-kubernetes/blob/main/02-distributed/distributed-docker.md).


I will be using minikube which quickly sets up a local Kubernetes cluster on macOS, Linux, and Windows. The first thing to do is to start your cluster. 
From a terminal with administrator access, run the following command

```bash
minikube start
```

The Pre-requisites to run the apps locally are the following:
* Docker
* node 12.* 