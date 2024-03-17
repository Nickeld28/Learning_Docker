## Creating a nginx container

Let's create a container from the `nginx` image with the command:

    docker run nginx

An nginx web server will be deployed inside the container, which can be used to provide access to static files - images, HTML, CSS or Java Script files, etc.

The nginx image consists of different layers, which are downloaded separately as archives and then unpacked. The IDs of each layer are indicated.

After starting the container, the terminal was automatically connected to the process inside the container and some output was displayed, which is essentially the logs of the running nginx server.

The command line is not ready to accept commands in its current state. You can view running containers in another terminal window.

It is currently not possible to connect to the nginx web server with a webbrowser. The webserver uses port 80, but there is no access to it now, but the container continues to work.

### First run example:

<details>

```bash
nickeld28@DockerVM:~$ docker run nginx
Unable to find image 'nginx:latest' locally
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
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2024/03/17 07:25:49 [notice] 1#1: using the "epoll" event method
2024/03/17 07:25:49 [notice] 1#1: nginx/1.25.4
2024/03/17 07:25:49 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14) 
2024/03/17 07:25:49 [notice] 1#1: OS: Linux 6.5.0-1016-azure
2024/03/17 07:25:49 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2024/03/17 07:25:49 [notice] 1#1: start worker processes
2024/03/17 07:25:49 [notice] 1#1: start worker process 29
2024/03/17 07:25:49 [notice] 1#1: start worker process 30
2024/03/17 07:25:49 [notice] 1#1: start worker process 31
2024/03/17 07:25:49 [notice] 1#1: start worker process 32
2024/03/17 07:25:49 [notice] 1#1: start worker process 33
2024/03/17 07:25:49 [notice] 1#1: start worker process 34
2024/03/17 07:25:49 [notice] 1#1: start worker process 35
2024/03/17 07:25:49 [notice] 1#1: start worker process 36
```

</details>

Stopped the container using a keyboard shortcut <kbd>Ctrl</kbd> + <kbd>C</kbd>.

To prevent the terminal from automatically connecting to the container upon startup, I will run it in the detached mode:

    docker run -d nginx

### Example of running in the detached mode:

<details>

```bash
nickeld28@DockerVM:~$ docker run -d nginx
0b994de9393645ac0527cc30397a311a56249659c169c8a0e2a8a624df7663a0
nickeld28@DockerVM:~$ 
```
```bash
nickeld28@DockerVM:~$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS     NAMES
0b994de93936   nginx     "/docker-entrypoint.…"   14 minutes ago   Up 14 minutes   80/tcp    frosty_joliot
```

</details>

To try to connect to the web server, I try to find out its IP address:

    docker inspect 0b994de93936 | grep IPAddress

### Example of finding a server IP address in a container:

<details>

```bash
nickeld28@DockerVM:~$ docker inspect 0b994de93936 | grep IPAddress
            "SecondaryIPAddresses": null,
            "IPAddress": "172.17.0.2",
                    "IPAddress": "172.17.0.2",
nickeld28@DockerVM:~$ 
```

</details>

### Example of forced stopping of a container:

<details>

```bash
nickeld28@DockerVM:~$ docker kill frosty_joliot 
frosty_joliot
nickeld28@DockerVM:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES 
```

</details>

Let's create and launch a new container with a custom name:

    docker run -d --name my_nginx nginx

### Example of creating a container with the specified name:

<details>

```bash
nickeld28@DockerVM:~$ docker run -d --name my_nginx nginx
b81ed97a92c4f461839f1d87be695cf1fae3afbe388c40ae9eebeed3516a42f2
nickeld28@DockerVM:~$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS     NAMES
b81ed97a92c4   nginx     "/docker-entrypoint.…"   7 seconds ago   Up 7 seconds   80/tcp    my_nginx
nickeld28@DockerVM:~$ 
```

</details>

To connect to a running container, you can create a new process in it and launch a shell:

    docker exec -it b81ed97a92c4 bash

And then I want to see the contents of the nginx start html page.

### Example of connecting to a running container by executing a command:

<details>

```bash
nickeld28@DockerVM:~$ docker exec -it b81ed97a92c4 bash
root@b81ed97a92c4:/# hostname
b81ed97a92c4
root@b81ed97a92c4:/# hostname -i
172.17.0.2
root@b81ed97a92c4:/# ls
bin   dev		   docker-entrypoint.sh  home  lib64  mnt  proc  run   srv  tmp  var
boot  docker-entrypoint.d  etc			 lib   media  opt  root  sbin  sys  usr
root@b81ed97a92c4:/# cd /usr/share/nginx/html
root@b81ed97a92c4:/usr/share/nginx/html# ls -la
total 16
drwxr-xr-x 2 root root 4096 Mar 12 01:55 .
drwxr-xr-x 3 root root 4096 Mar 12 01:55 ..
-rw-r--r-- 1 root root  497 Feb 14 16:03 50x.html
-rw-r--r-- 1 root root  615 Feb 14 16:03 index.html
root@b81ed97a92c4:/usr/share/nginx/html# cat index.html 
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
root@b81ed97a92c4:/usr/share/nginx/html# exit
exit
nickeld28@DockerVM:~$ 

```

</details>

I know the server's IP address, I try to connect through a browser to the server using the URL `https://172.17.0.2/` via HTTP and *(default port 80)*, but without success.

### Failed attempt to connect to the server in the container:

<details>

>### Unable to connect
>
>An error occurred during a connection to 172.17.0.2.
>
>* The site could be temporarily unavailable or too busy. Try again in a few moments.
>* If you are unable to load any pages, check your computer’s network connection.
>* If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the Web.

</details>

To be able to connect to the server, you need to publish the container port, i.e. map the host port where docker is installed with the container port.

I'll run a new container publishing port 80:

    docker run -d -p 8080:80 nginx

### Example of running a container with an open port:

<details>

```bash
nickeld28@DockerVM:~$ docker run -d -p 8080:80 nginx
1eba2df585ef852fafc9b9eef975449d2d7c48a63ed73a35a7b52f9ae62fca38
```

```
http://127.0.0.1:8080/

Welcome to nginx!

If you see this page, the nginx web server is successfully installed and working. Further configuration is required.

For online documentation and support please refer to nginx.org.
Commercial support is available at nginx.com.

Thank you for using nginx.
```

</details>

Outer ports that have already been used cannot be used for mapping; only free ports can be used.

I'm trying to start a new container publishing port 80 with the same external port as another running container:

    docker run -d -p 8080:80 nginx

### Failed attempt to create a container using a busy port:

<details>

```bash
nickeld28@DockerVM:~$ docker run -d -p 8080:80 nginx
a6b0d395d1c2ffdee5b47c8b40e9488741f69b068c20da06184328a348e23794
docker: Error response from daemon: driver failed programming external connectivity on endpoint pensive_hamilton (7eb59c010f5a6d60dbdaa7bd0863c0d5d4b07ad46d643d682f90f915b844a72e): Bind for 0.0.0.0:8080 failed: port is already allocated.
```

</details>

#### [<<< Back](/Summary.md)
