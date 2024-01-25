# DevOps - Lemoncode - Kubernetes Exercises
1. [Introduction](#intro)

<a name="intro"></a>
## 1. Introduction

We've been asked by LemonCode team to implement the solution of these three exercises:
* Exercise 1. Monolith in memory
    * This is a web app that exposes an UI app (the typical to-do list app), and an API to manage in the server the 'TODOS'. 

    * The TODOS persistency is in-memory, which means that the data is lost when app is closed. 

    * To build the image of this app, look at the steps provided by lemoncode in [00-monolith-in-mem/README.md](https://github.com/Lemoncode/bootcamp-devops-lemoncode/blob/master/02-orquestacion/exercises/00-monolith-in-mem/README.md).

    * You can see the instructions from LemonCode in [exercise monolith in memory](https://github.com/Lemoncode/bootcamp-devops-lemoncode/blob/master/02-orquestacion/exercises/00-monolith-in-mem/exercise-monolith-in-memory.md).

* Exercise 2. Monolith
    * Same app but in this case, the in-memory persistency is done through a database.

    * To run the app locally you can follow the steps provided by lemoncode in [01-monolith/README.md](https://github.com/Lemoncode/bootcamp-devops-lemoncode/blob/master/02-orquestacion/exercises/01-monolith/README.md).

    * You can see the instructions from LemonCode in [exercise monolith](https://github.com/Lemoncode/bootcamp-devops-lemoncode/blob/master/02-orquestacion/exercises/01-monolith/exercise-monolith.md).

* Exercise 3. Distributed Application
    * There are two apps, one UI exposed via an nginx and one express/nodejs API that connects to a postgres database.

    * To run the app locally you can follow the steps provided by lemoncode in [02-distributed/README.md](https://github.com/Lemoncode/bootcamp-devops-lemoncode/blob/master/02-orquestacion/exercises/02-distributed/README.md).

    * You can see the instructions from LemonCode in [exercise-ingress](https://github.com/Lemoncode/bootcamp-devops-lemoncode/blob/master/02-orquestacion/exercises/02-distributed/exercise-ingress.md).

I will be using minikube which quickly sets up a local Kubernetes cluster on macOS, Linux, and Windows. 
The first thing to do is to start your cluster. 
From a terminal with administrator access, run the following command

```bash
minikube start
```

The Pre-requisites to run the apps locally are the following:
* Docker
* node 12.* 