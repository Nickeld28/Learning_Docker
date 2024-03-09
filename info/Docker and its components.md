## What is Docker?

**Docker** is a service for running applications in containers.

## What are the benefits of Docker?

* Applications run in an isolated environment - in containers. Each container is isolated from the external environment and from other containers. Applications running in containers do not depend on what is located outside the containers.

* Easily run applications on different servers. Using a Docker image, you can deploy applications on different computers, and the applications will behave exactly the same on different servers.

* All application dependencies are installed inside containers.

* Applications inside containers can be easily scaled by increasing the number of containers.

* It is very convenient to use Docker in the application development process and for this you do not need to install the necessary dependencies on your computer, they will all be inside containers. Individual application components can optionally be installed in separate containers.

## Docker Components

* **Docker engine**
* **Client**
* **Daemon**
* **Host**
* **Container**
* **Image**
* **Repository**
* **Registry**

**Docker engine** is a client-server application that exists in two variations:

* ___Docker Community Edition (CE)___ - free software
* ___Docker Enterprise___ - paid version of the engine

**The client** runs on the command line and connects to the Docker service, which can run either locally or remotely.

**Service** is responsible for creating containers and processing requests from clients - Docker Server.

**Host** is the computer on which docker is running, i.e. the service is located.

**Container** is the smallest entity in Docker. This is a Linux-based virtual environment with a minimum set of required components to run the application.

Typically, a single application requires its own personal container (*Single Purpose*), but there are exceptions to this rule.

**Image** is the basis for creating containers.

**Repository** - storage of images and their versions.

**Registry** - information about repositories. The registry can be local or remote.

DockerHub is the most popular remote registry.

#### [<<< Back](/Summary.md)
