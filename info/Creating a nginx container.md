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

#### [<<< Back](/Summary.md)
