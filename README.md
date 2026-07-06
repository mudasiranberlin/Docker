# Docker Commands Cheat Sheet

A quick reference guide covering Docker installation, service management, image/container operations, and common day-to-day commands.

## Table of Contents
- [Installation](#installation)
- [Managing the Docker Service](#managing-the-docker-service)
- [Working with Images](#working-with-images)
- [Working with Containers](#working-with-containers)
- [Named Containers](#named-containers)
- [Container Lifecycle Management](#container-lifecycle-management)
- [Cleanup](#cleanup)

---

## Installation

Install Docker using `yum` (RHEL/CentOS-based systems):

```bash
yum install docker
```

---

## Managing the Docker Service

Check the current status of the Docker service:

```bash
service docker status
```

View system-wide Docker information (containers, images, storage driver, etc.):

```bash
docker info
```

Start the Docker service:

```bash
service docker start
```

Confirm the service started successfully:

```bash
service docker status
```

Check Docker info again once the service is running:

```bash
docker info
```

---

## Working with Images

List all locally available images:

```bash
docker images
```

Pull a specific image from Docker Hub:

```bash
docker pull chef/chef:18.11.7-amd64
docker pull jenkins/jenkins
```

Search Docker Hub for available images:

```bash
docker search chef
```

---

## Working with Containers

List running containers:

```bash
docker ps
```

List all containers (including stopped ones):

```bash
docker ps -a
```

Run a container interactively with a shell (Ubuntu example):

```bash
docker run -it ubuntu /bin/bash
```

Inside the container, check the OS release info:

```bash
cat /etc/os-release
```

Exit the container shell:

```bash
exit
```

---

## Named Containers

Create and name containers for easier reference:

```bash
docker run -it --name muzamil ubuntu /bin/bash
docker run -it --name mudasir ubuntu /bin/bash
```

Start a previously created (stopped) named container:

```bash
docker start muzamil
```

Run a container in detached mode (background):

```bash
docker run -d muzamil
```

Attach your terminal to a running container's process:

```bash
docker attach muzamil
```

Check status of all containers again:

```bash
docker ps -a
```

---

## Container Lifecycle Management

Stop a running container:

```bash
docker stop mudasir
```

Remove a stopped container:

```bash
docker rm mudasir
```

Force remove a container (even if running):

```bash
docker rm -f mudasir
```

---

## Cleanup

Remove all stopped containers to free up space:

```bash
docker container prune
```

---

## Notes

- `docker ps -a` is your go-to command to see **all** containers, running or not.
- `docker run -it <image> /bin/bash` creates a **new** container each time — use `docker start` + `docker attach` to reuse an existing one.
- Use `--name` when running containers so they're easier to manage instead of relying on random Docker-generated names.
- `docker rm -f` skips the need to `stop` first, but use with caution.

---

## License

Feel free to use and modify this cheat sheet for personal or educational purposes.




# Docker


yum install docker

service docker status


docker info 

service docker start

service docker status 

docker info 

docker images

docker ps 

docker ps -a

docker run -it ubuntu /bin/bash

 cat /etc/os-release

exit

docker images

docker run -it ubuntu /bin/bash

docker ps -a

docker pull chef/chef:18.11.7-amd64

docker pull jenkins/jenkins

docker search chef

docker run -it --name muzamil ubuntu /bin/bash

docker run -it --name mudasir ubuntu /bin/bash

docker start muzamil

docker run -d muzamil

docker attach muzamil

docker ps -a

docker stop mudasir

docker rm mudasir 

docker rm -f mudasir 

docker container prune 
