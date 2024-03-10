## How containers work

Containers are created on a host machine running the GNU/Linux operating system.

### Docker uses host resources:

* Linux Kernel
* Random access memory (RAM)
* Processor (CPU)
* Disk space (HDD, SSD, NVMe)
* Network

### What happens when containers are created:

* Files are created on disk that are accessible only to the target container.
* Each container runs one process (but there can be more), independent of processes in other containers.
* All created containers use common computer resources: Linux kernel, RAM, CPU and Network.

### Efficient disk usage:

 If containers are created from the same or similar images, then such containers may have common files on disk. The files will not be copied many times when launching multiple containers from one image, but will be reused from one place.

### What happens when containers stop:

* When containers are stopped, the processes in them are terminated and host resources are freed, including disk space that was used by the containers.
* Docker automatically stops containers that have no active processes. If a process in a container has completed a task and exited, then docker will stop that container.

### How does Docker work on other OS?

For other systems (Mac OS, Windows), Docker Desktop is used, which is based on a virtual machine running GNU/Linux and Docker runs on this host.

#### [<<< Back](/Summary.md)
