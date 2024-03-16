## Creating a hello-world container

Let's create a container from the `hello-world` image with the command:

    docker run hello-world

Docker first tries to find the `hello-world` image locally and if it exists, then a container is created and launched from it.

If there is no such image locally, then Docker will try to find this image on Docker Hub. If found, the image will be downloaded and saved locally, and then the container will be created and launched.

If no tag is specified for the image, the `latest` tag is used by default.

Information about the [hello-world image](https://hub.docker.com/_/hello-world) can be found on Docker Hub.

The process inside the created container generated text and output it to the terminal and ended there, and the docker stopped the container after that, because there were no longer active processes inside the container.

#### First run example:

<details>

```bash
nickeld28@DockerVM:~$ docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
nickeld28@DockerVM:~$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
c1ec31eb5944: Pull complete 
Digest: sha256:6352af1ab4ba4b138648f8ee88e63331aae519946d3b67dae50c313c6fc8200f
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

```

</details>

\
When you re-create a container from an image that has already been downloaded, the process will happen a little faster, without the stage of downloading and saving the image.

#### Restart example:

<details>

```bash
nickeld28@DockerVM:~$ docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

</details>

#### [<<< Back](/Summary.md)
