# Install Docker

#### Installation instructions on the [official Docker website](https://docs.docker.com/engine/install/)

## [Ubuntu](https://docs.docker.com/engine/install/ubuntu/)

### 1. You need to check the system version

#### Use any of these commands:

* `lsb_release -a`

* `cat /etc/os-release`

* `hostnamectl`


#### Here is my system version:

- Operating System: Ubuntu 22.04.4 LTS              
- Kernel: Linux 6.5.0-1016-azure
- Architecture: x86-64

### 2. Make sure the system meets the requirements

The version of my operating system matches the requirements in the documentation.

### 3. Uninstall previous versions of Docker

```bash
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

### 4. Install Docker apt repositories

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

### 5. Install the required Docker packages

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### 6. Make sure Docker is running successfully

#### You can check the Docker version:

    sudo docker version

This is my conclusion:

<details>

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
    
</details>

 #### It is recommended to launch the hello-world image:

    sudo docker run hello-world

Successful result:

<details>

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

</details>

#### [<<< Back](/Summary.md)
