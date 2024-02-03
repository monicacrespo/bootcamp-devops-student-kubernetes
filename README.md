# DevOps - Lemoncode - Kubernetes Exercises
1. [Introduction](#intro)

<a name="intro"></a>
## 1. Introduction

We've been asked by LemonCode team to implement the solution of these [three exercises](https://github.com/Lemoncode/bootcamp-devops-lemoncode/tree/master/02-orquestacion/exercises):
* Exercise 00. Monolith in memory
    * This is a web app that exposes an UI app (the typical to-do list app), and an API to manage in the server the 'TODOS'. 

    * The TODOS persistency is in-memory, which means that the data is lost when app is closed.     

    * You can see the solution in [00-monolith-in-mem/README.md](https://github.com/monicacrespo/bootcamp-devops-student-kubernetes/tree/main/00-monolith-in-mem/README.md).

* Exercise 01. Monolith
    * Same app but in this case, the in-memory persistency is done through a database.  

    * You can see the solution in [01-monolith/README.md](https://github.com/monicacrespo/bootcamp-devops-student-kubernetes/tree/main/01-monolith/README.md).

* Exercise 02. Distributed Application
    * There are two apps, one UI exposed via an nginx and one express/nodejs API that connects to a postgres database.

    * You can see the solution in [02-distributed/README.md](https://github.com/monicacrespo/bootcamp-devops-student-kubernetes/tree/main/02-distributed/README.md).


I will be using minikube with docker driver, which quickly sets up a local Kubernetes cluster on macOS, Linux, and Windows. The first thing to do is to start your cluster. 
From a terminal with administrator access, run the following command

```bash
minikube start --driver=docker
```

The Pre-requisites to run the apps locally are the following:
* Docker
* node 12.* 