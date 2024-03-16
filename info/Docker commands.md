## Docker commands

Docker commands require the use of `sudo`. There is a way to set it up so that you can enter commands without `sudo`.

### Using Docker commands without `sudo`

To avoid typing sudo every time you run Docker commands, you can add the user to the docker group:

```bash
sudo usermod -aG docker ${USER}
```

To apply changes to the group, you need to log in or run the command and enter the password:

```bash
su - ${USER}
```

You can check that the user is added to the docker group like this:

```bash
id -nG
```

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ sudo usermod -aG docker ${USER}
nickeld28@DockerVM:~$ id -nG
nickeld28@DockerVM:~$ su - ${USER}
Password: 
nickeld28@DockerVM:~$ id -nG
nickeld28 adm cdrom sudo dip plugdev lpadmin lxd sambashare docker
nickeld28@DockerVM:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

</details>

### 1. Show Docker client information

* `docker -v`
* `docker --version`

#### Мy examples:

<details>

```bash
nickeld28@DockerVM:~$ docker -v
Docker version 25.0.4, build 1a576c5
```

</details>

<details>

```bash
nickeld28@DockerVM:~$ docker --version
Docker version 25.0.4, build 1a576c5
```

</details>

### 2. Show information about Docker client and Docker server versions

* `docker version`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker version
Client: Docker Engine - Community
Version:           25.0.4
API version:       1.44
Go version:        go1.21.8
Git commit:        1a576c5
Built:             Wed Mar  6 16:32:12 2024
OS/Arch:           linux/amd64
Context:           default

Server: Docker Engine - Community
Engine:
Version:          25.0.4
API version:      1.44 (minimum version 1.24)
Go version:       go1.21.8
Git commit:       061aa95
Built:            Wed Mar  6 16:32:12 2024
OS/Arch:          linux/amd64
Experimental:     false
containerd:
Version:          1.6.28
GitCommit:        ae07eda36dd25f8a1b98dfbf587313b99c0190bb
runc:
Version:          1.1.12
GitCommit:        v1.1.12-0-g51d5e94
docker-init:
Version:          0.19.0
GitCommit:        de40ad0
```

</details>

### 3. Show a list of running containers

* `docker ps`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

</details>

### 4. Show a list of running and stopped containers

* `docker ps -a`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED              STATUS                          PORTS     NAMES
425f7f79867b   hello-world   "/hello"   About a minute ago   Exited (0) About a minute ago             adoring_jones
```

</details>

### 5. Show a list of local images

* `docker images`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker images
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
hello-world   latest    d2c94e258dcb   10 months ago   13.3kB
```

</details>

### 6. Creating and running a container from an image

* `docker run <image_name>`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker run busybox
Unable to find image 'busybox:latest' locally
latest: Pulling from library/busybox
7b2699543f22: Pull complete 
Digest: sha256:650fd573e056b679a5110a70aabeb01e26b76e545ec4b9c70a9523f2dfaf18c6
Status: Downloaded newer image for busybox:latest
```

</details>

### 7. Download the image and save locally

* `docker pull <image_name>`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
8a1e25ce7c4f: Pull complete 
e78b137be355: Pull complete 
39fc875bd2b2: Pull complete 
035788421403: Pull complete 
87c3fb37cbf2: Pull complete 
c5cdd1ce752d: Pull complete 
33952c599532: Pull complete 
Digest: sha256:6db391d1c0cfb30588ba0bf72ea999404f2764febf0f1f196acd5867ac7efa7e
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest

```

</details>

### 8. Removing a container

* `docker rm <container_id>`
* `docker rm <container_name>`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker ps -a
CONTAINER ID   IMAGE                COMMAND    CREATED          STATUS                      PORTS     NAMES
85b50b027080   hello-world:latest   "/hello"   18 seconds ago   Exited (0) 17 seconds ago             happy_pascal
3ca6e48096a5   hello-world          "/hello"   41 seconds ago   Exited (0) 41 seconds ago             epic_dijkstra
nickeld28@DockerVM:~$ docker rm epic_dijkstra 
epic_dijkstra
nickeld28@DockerVM:~$ docker rm 85b50b027080
85b50b027080
nickeld28@DockerVM:~$ docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

```

</details>

#### [<<< Back](/Summary.md)
