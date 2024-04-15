# Docker Commands

## Table of contents

- [Docker Commands](#docker-commands)
  - [Table of contents](#table-of-contents)
  - [⬇️Install Docker⬇️](#️install-docker️)
  - [🎓Basic commands🎓](#basic-commands)
    - [List docker processes](#list-docker-processes)
    - [List docker containers](#list-docker-containers)
    - [Start container](#start-container)
    - [Stop container](#stop-container)
    - [Delete container](#delete-container)
    - [Execute command in container](#execute-command-in-container)
    - [Copy file from/to a container](#copy-file-fromto-a-container)
  - [🐝Docker Swarm🐝](#docker-swarm)
    - [List nodes](#list-nodes)
    - [Create docker network](#create-docker-network)
    - [Create docker service](#create-docker-service)
    - [Scale Service](#scale-service)
  - [📀Docker images📀](#docker-images)
    - [Pull image](#pull-image)
    - [Build Dockerfile (in the same directory as the Dockerfile)](#build-dockerfile-in-the-same-directory-as-the-dockerfile)
    - [List docker images](#list-docker-images)
    - [Remove docker image](#remove-docker-image)

## ⬇️Install Docker⬇️

[On Ubuntu](https://docs.docker.com/engine/install/ubuntu/ "https://docs.docker.com/engine/install/ubuntu/")

## 🎓Basic commands🎓

### List docker processes

```bash
docker ps
```

### List docker containers

```bash
docker container ls
```

Options:

- Include stopped containers: ``-a``

### Start container

```bash
docker run <image>:<tag>
```

Options:

- Expose port: ``-p <host-port>:<container-port>``
- Mount volume: ``-v <host-path>:<container-path>``

You can also use [Docker compose](Docker_Compose.md#docker-compose)

### Stop container

```bash
docker container stop <container-id>
```

### Delete container

```bash
docker container rm <container-id>
```

### Show container logs

```bash
docker container logs <container-id>
```

Options:

- Follow logs: `-f` or `--follow`
- Get last n lines: `-n` or `--tail <number-of-lines>`
- Add timestamps: `--timestamps`
- Get logs since a specific point in time: `--since <time/timestamp/XhXmXs>`
- Get logs until a specific point in time: `--since <time/timestamp/XhXmXs>`
### Execute command in container

``` bash
docker exec -it <container> <command>
```

### Copy file from/to a container

```bash
sudo docker cp <source-path> <destination-path>
```

---

## 🐝Docker Swarm🐝

### List nodes

```bash
docker node ls
```

### Create docker network

```bash
docker network create --driver=overlay <name>
```

### Create docker service

```bash
docker service create --name=<service-name> <image>:<tag>
```

Options:

- Use a network: ``--network=<network-name>``
- Expose a port: ``-p <host-port>:<container-port>``
- Pass environnement variable: ``-e <variable-name>=<value>``
- Mount a volume: ``--mount type=bind,source="<host-path>",target="<container-path>"``

### Scale Service

```bash
docker service scale <service-name>=<number-of-replicas>
```

---

## 📀Docker images📀

[Dockerhub](https://hub.docker.com/)

### Pull image

```bash
docker pull <image>:<tag>
```

### Build Dockerfile (in the same directory as the Dockerfile)

```bash
docker build -t <image-name>:<tag> .
```

### List docker images

```bash
docker images
```

### Remove docker image

```bash
docker image rm <image-id>
```
