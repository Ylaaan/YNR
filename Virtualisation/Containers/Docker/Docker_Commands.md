/commi
## Install Docker 

[On Ubuntu](https://docs.docker.com/engine/install/ubuntu/ "https://docs.docker.com/engine/install/ubuntu/")

## Basic commands 

##### List docker processes

```bash
docker ps
```

##### List docker containers

```bash
docker container ls
```

Options : 
- Include stopped containers : ``-a``

##### Start container

```bash
docker run [image]:[tag]
```

Options :
- Expose port : ``-p [host-port]:[container-port]``
- Mount volume : ``-v [host-path]:[container-path]``

##### Stop container

```bash
docker container stop [container-id]
```

##### Delete container

```bash
docker container rm [container-id]
```

##### Execute command in container

``` bash
docker exec -it [container] [command]
```

##### Copy file from/to a container

```bash
sudo docker cp [source-path] [destination-path]
```

---

## Docker Swarm

##### List nodes

```bash
docker node ls
```

##### Create docker network
```bash
docker network create --driver=overlay [name]
```

##### Create docker service

```bash
docker service create --name=[service-name] [image]:[tag]
```

Options : 
- Use a network : ``--network=[network-name]``
- Expose a port : ``-p [host-port]:[container-port]``
- Pass environnement variable : ``-e [variable-name]=[value]``
- Mount a volume : ``--mount type=bind,source="[host-path]",target="[container-path]"``

##### Scale Service

```bash
docker service scale [service-name]=[number-of-replicas]
```

---

## Docker images

[Dockerhub](https://hub.docker.com/)

##### Pull image

```bash
docker pull [image]:[tag]
```

##### Build Dockerfile (in the same directory as the Dockerfile)

```bash
docker build -t [image-name]:[tag] .
```

##### List docker images

```bash
docker images
```

##### Remove docker image

```bash
docker image rm [image-id]
```
