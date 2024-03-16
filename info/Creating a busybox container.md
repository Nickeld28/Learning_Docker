## Creating a busybox container

Let's create a container from the `busybox` image with the command:

    docker run busybox

The `busybox` image allows you to create a simple Linux container.

The container started and was stopped. Inside the container there was a "sh" command - launching a shell, but the process ended because there was no connection and the result of the shell was not transmitted anywhere.

#### First run example:

<details>

```bash
nickeld28@DockerVM:~$ docker run busybox
Unable to find image 'busybox:latest' locally
latest: Pulling from library/busybox
7b2699543f22: Pull complete 
Digest: sha256:650fd573e056b679a5110a70aabeb01e26b76e545ec4b9c70a9523f2dfaf18c6
Status: Downloaded newer image for busybox:latest

nickeld28@DockerVM:~$ docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED              STATUS                          PORTS     NAMES
0b10066e3efe   busybox       "sh"       About a minute ago   Exited (0) About a minute ago             sharp_varahamihira
069cb0b3e228   hello-world   "/hello"   2 hours ago          Exited (0) 2 hours ago                    reverent_galileo

nickeld28@DockerVM:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

</details>

\
To keep the container running, you need to connect to its process:

    docker run -it busybox

Inside the container, you can find out the container hostname with the command:

    hostname

The IP address of the container can be found with the command:

    hostname -i

#### Restart example:

<details>

```bash
nickeld28@DockerVM:~$ docker run -it busybox
/ # ls
bin    etc    lib    proc   sys    usr
dev    home   lib64  root   tmp    var
/ # hostname
bc98423639e3
/ # hostname -i
172.17.0.2
/ # exit
```

</details>

#### [<<< Back](/Summary.md)
