# Docker Cheat Sheet

Docker registry: https://hub.docker.com/explore/
This cheat sheet is built on: https://docker-curriculum.com/

```bash
# List help commands
$ docker run --help
```
```bash
# Create a container, run docker image 'hello-world' (https://hub.docker.com/_/hello-world/)
$ docker run hello-world
```
```bash
# Pull docker image busybox (https://hub.docker.com/_/busybox/)
$ (sudo) docker pull busybox
```
```bash
# Download specific ubuntu version
$ docker pull ubuntu:14.04
```
```bash
# Show all docker images
$ docker images
```
```bash
# Create a container and run it
$ docker run busybox
```
```bash
# Pull busybox, create a container and run it directly in the shell
$ docker run -it --rm busybox
```
```bash
# Create a container, run busybox and execute a command
$ docker run busybox echo 'Hello, nice to meet you!'
```
```bash
# List all docker processes (even the exited ones)
$ docker ps -a
```
```bash
# Download Ubuntu (latest) and/or run the container and drop into shell with bash
$ docker run -it ubuntu bash
```
```bash
# Run busybox container interactively with sh
$ docker run -it busybox sh
```
```bash
# Delete container with specific container ID
$ docker rm <container_id>
```
```bash
# Delete containers that have the status 'exited' (-q = return numeric id / -f = fiter)
$ docker rm $(docker ps -a -q -f status=exited)
```
```bash
# Download and/or run author/image_name in detached mode (-d), give it a name ('static-site') and expose port (-P)
$ docker run -d -P --name static-site user/image_name
```
```bash
# Show port of the container 'static-site'
$ docker port static-site

# 443/tcp -> 0.0.0.0:32768 => https://localhost:32768/
# 80/tcp -> 0.0.0.0:32769 # => http://localhost:32769/
```
```bash
# Specify port by forwarding the port to 8888
$ docker run -p 8888:80 user/image_name
# => http://localhost:8888/
```
```bash
# Stop detached container
$ docker stop <container_id>
```

Dockerfile (example):

```bash
# Instructions copied from - https://hub.docker.com/_/python/
FROM python:3-onbuild

# tell the port number the container should expose
EXPOSE 5000

# run the command
CMD ["python", "./app.py"]
```

```bash
# Build an image using a repo from the registry (e.g. 28374749/dockertest). Make sure a Dockerfile exists in the same directory)
$ docker build -t user/image_name .

# Run specific docker image on port 5000 (according to Dockerifle)
$ docker run -p 8888:5000 user/image_name
```

```bash
# Publish changes to the repo
$ docker push user/image_name
```

```bash
# Log in to your docker hub accou$ docker login
$ docker login
```

```bash
# Search for a specific image_name (e.g. elasticsearch)
$ docker search elasticsearch
```

```bash
# List all networks
$ docker network ls 
```
