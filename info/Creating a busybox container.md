## Creating a busybox container

Let's create a container from the `busybox` image with the command:

    docker run busybox

The `busybox` image allows you to create a simple Linux container.

The container started and was stopped. Inside the container there was a "sh" command - launching a shell, but the process ended because there was no connection and the result of the shell was not transmitted anywhere.

### First run example:

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

### Restart with connecting example:

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

\
With this connection, the `sh` shell waits for commands and the container continues to run.
You can verify this by looking at what containers are running in another terminal window.

### Example of checking a running container:

<details>

```bash
nickeld28@DockerVM:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED         STATUS         PORTS     NAMES
bc98423639e3   busybox   "sh"      6 seconds ago   Up 5 seconds             zen_gauss
```

</details>

### Example of checking Internet access:

You need to make sure that the DNS and Google server responds, which means there is access to the Internet.

<details>

```bash
nickeld28@DockerVM:~$ docker run -it busybox
/ # ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8): 56 data bytes
64 bytes from 8.8.8.8: seq=0 ttl=107 time=6.776 ms
64 bytes from 8.8.8.8: seq=1 ttl=107 time=7.386 ms
^C
--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 packets received, 0% packet loss
round-trip min/avg/max = 6.776/7.081/7.386 ms
/ # ping google.com
PING google.com (209.85.233.139): 56 data bytes
64 bytes from 209.85.233.139: seq=0 ttl=107 time=19.401 ms
64 bytes from 209.85.233.139: seq=1 ttl=107 time=18.977 ms
^C
```

</details>

#### [<<< Back](/Summary.md)
