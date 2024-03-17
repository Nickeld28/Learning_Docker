# Docker commands

Docker commands require the use of `sudo`. There is a way to set it up so that you can enter commands without `sudo`.

## Using Docker commands without `sudo`

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

## 1. Show information

## 1.1. Show Docker client information

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

### 1.2. Show information about Docker client and Docker server versions

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

### 1.3. Show a list of running containers

* `docker ps`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

</details>

### 1.4. Show a list of running and stopped containers

* `docker ps -a`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED              STATUS                          PORTS     NAMES
425f7f79867b   hello-world   "/hello"   About a minute ago   Exited (0) About a minute ago             adoring_jones
```

</details>

### 1.5. Show a list of local images

* `docker images`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker images
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
hello-world   latest    d2c94e258dcb   10 months ago   13.3kB
```

</details>

### 1.6. Show low-level information on Docker object:

* `docker inspect <docker_object>`

#### Example container information:

<details>

```bash
nickeld28@DockerVM:~$ docker inspect 5299500decf3
[
    {
        "Id": "5299500decf357a7e684b96ba62ad55c101b36fdc9fb12a0d4399bec08287e4d",
        "Created": "2024-03-17T08:50:29.626389178Z",
        "Path": "/hello",
        "Args": [],
        "State": {
            "Status": "exited",
            "Running": false,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 0,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2024-03-17T08:50:29.907917432Z",
            "FinishedAt": "2024-03-17T08:50:29.908546831Z"
        },
        "Image": "sha256:d2c94e258dcb3c5ac2798d32e1249e42ef01cba4841c2234249495f87264ac5a",
        "ResolvConfPath": "/var/lib/docker/containers/5299500decf357a7e684b96ba62ad55c101b36fdc9fb12a0d4399bec08287e4d/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/5299500decf357a7e684b96ba62ad55c101b36fdc9fb12a0d4399bec08287e4d/hostname",
        "HostsPath": "/var/lib/docker/containers/5299500decf357a7e684b96ba62ad55c101b36fdc9fb12a0d4399bec08287e4d/hosts",
        "LogPath": "/var/lib/docker/containers/5299500decf357a7e684b96ba62ad55c101b36fdc9fb12a0d4399bec08287e4d/5299500decf357a7e684b96ba62ad55c101b36fdc9fb12a0d4399bec08287e4d-json.log",
        "Name": "/quizzical_heyrovsky",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "docker-default",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "ConsoleSize": [
                24,
                80
            ],
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "private",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": [],
            "BlkioDeviceWriteBps": [],
            "BlkioDeviceReadIOps": [],
            "BlkioDeviceWriteIOps": [],
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": null,
            "PidsLimit": null,
            "Ulimits": [],
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware",
                "/sys/devices/virtual/powercap"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/1a1d867cfd0e0a058835db5441b83137f4fbd71ea51a9149a763b74bfeb87ba4-init/diff:/var/lib/docker/overlay2/a1d554c0d91292722238e9147b4e0a6f94f8a15ee7274161d52e097a45534a07/diff",
                "MergedDir": "/var/lib/docker/overlay2/1a1d867cfd0e0a058835db5441b83137f4fbd71ea51a9149a763b74bfeb87ba4/merged",
                "UpperDir": "/var/lib/docker/overlay2/1a1d867cfd0e0a058835db5441b83137f4fbd71ea51a9149a763b74bfeb87ba4/diff",
                "WorkDir": "/var/lib/docker/overlay2/1a1d867cfd0e0a058835db5441b83137f4fbd71ea51a9149a763b74bfeb87ba4/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "5299500decf3",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": true,
            "AttachStderr": true,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/hello"
            ],
            "Image": "hello-world",
            "Volumes": null,
            "WorkingDir": "/",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {}
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "017ff0f47931fdd62cf39196e64c19e47260285d88b3d35b9761abca023f8e94",
            "SandboxKey": "/var/run/docker/netns/017ff0f47931",
            "Ports": {},
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "",
            "Gateway": "",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "",
            "IPPrefixLen": 0,
            "IPv6Gateway": "",
            "MacAddress": "",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "MacAddress": "",
                    "NetworkID": "1e72fc86dd276d31d5ba662353719a81f215b6a78ace87a85a8c3f900b4067e3",
                    "EndpointID": "",
                    "Gateway": "",
                    "IPAddress": "",
                    "IPPrefixLen": 0,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "DriverOpts": null,
                    "DNSNames": null
                }
            }
        }
    }
]
```

</details>

## 2. Actions with images

### 2.1. Download the image and save locally

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

## 3. Actions with containers

### 3.1. Creating and running a container from an image

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

### 3.2. Creating and running a container and connecting to it interactively with the terminal:

* `docker run -it <image_name>`

#### My example:

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

### 3.3. Creating and running a container in the detached mode:

* `docker run -d <image_name>`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker run -d nginx
34bd60ce3cd02df873ba57fa9c9cb40d49f4ef16dd23228ccd6c1205d16da259
nickeld28@DockerVM:~$ 
```

</details>

### 3.4. Stopping a container:

* `docker stop <container_id>`
* `docker stop <container_name>`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker stop bc98423639e3
bc98423639e3

nickeld28@DockerVM:~$ docker stop laughing_tesla 
laughing_tesla
```

</details>

### 3.5. Forced stopping of a container:

* `docker kill <container_id>`
* `docker kill <container_name>`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker kill frosty_joliot 
frosty_joliot
```

</details>

### 3.6. Removing a stopped container

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

### 3.7. Removing a running container:

* `docker rm -f <container_id>`
* `docker rm -f <container_name>`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED         STATUS         PORTS     NAMES
b03ecf604f30   busybox   "sh"      4 seconds ago   Up 4 seconds             sleepy_dhawan
nickeld28@DockerVM:~$ docker rm -f sleepy_dhawan
sleepy_dhawan
nickeld28@DockerVM:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

</details>

### 3.8. Removing all stopped containers

* `docker container prune`

#### My example:

<details>

```bash
nickeld28@DockerVM:~$ docker container prune
WARNING! This will remove all stopped containers.
Are you sure you want to continue? [y/N] y
Deleted Containers:
dd2368af00b27bd1d75c243caae9cd77fedf164a780259df3659d1a1eb88f472
000775ce25222fa2aeb3edb5d47ddbd16385af9505e637c9f788e374d88e3fac
9f99ff12370fe6866486de88f98ad0f5822b7ce2248039a4e25d8dea60578981
0b9190afb9ed48e80b1fe9e6d32d763e7127a164661e95c600c5a04c523243f1
bc98423639e3a39e66c4b47aec0efd6ffc6ab8931a90047a7001be94424af150
Total reclaimed space: 114B
```

</details>

#### [<<< Back](/Summary.md)
