## Kubernetes Exercises
The following exercises and source code to learn Kubernetes have been provided by Lemoncode here https://github.com/Lemoncode/bootcamp-devops-lemoncode/tree/master/02-orquestacion/exercises

### Pre-requisites to run the apps locally 
* Docker
* node 12.* >

### Exercise 1. Monolith in memory
* This is a web app that exposes an UI app (the typical to-do list app), and an API to manage in the server the 'TODOS'. 

* The TODOS persistency is in-memory, which means that the data is lost when app is closed. 

* To build the image of this app, look at the steps provided by lemoncode [here](00-monolith-in-mem/README.md).

* You can find the exercise 1 [here](00-monolith-in-mem/exercise-monolith-in-memory.md).

### Exercise 2. Monolith
* Same app but in this case, the in-memory persistency is done through a database.

* To run the app locally you can follow the steps provided by lemoncode [here](01-monolith/README.md).

* You can find the exercise 2 [here](01-monolith/exercise-monolith.md).


### Exercise 3. Distributed Application
* There are two apps, one UI exposed via an nginx and one express/nodejs API that connects to a postgres database.

* To run the app locally you can follow the steps provided by lemoncode [here](02-distributed/README.md).

* You can find the exercise 3 [here](02-distributed/exercise-ingress.md).