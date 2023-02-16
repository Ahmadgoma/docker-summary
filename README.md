# Docker summary

## Content:
  - [Docker](#docker)
  - [Advantage Of Docker](#advantage_of_docker)
  - [Container](#container)
  - [Image](#image)
  - [Registry](#registry)
  - [Docker Client](#client)
  - [Docker Daemon](#daemon)
  - [Docker Architecture](#architecture)
  - [Docker Commands](#commands)
  - [Dockerfile](#dockerfile)
  - [Docker Compose](#dockercompose)
  - [Docker Swarm](#dockerswarm)
  - [Kubarnetes](#k8s)
  - [Docker Commit](#dockerswarm)

**<a name="docker">
Docker
</a>**
- Is a free software, allows users to create isolated environments to launch and deploy its applications.
- These are called containers.
- Is a container management service.

**<a name="docker">
Advantage Of Docker Docker
</a>**
-  Lightweight.
-  Simple & Fast deployment.
-  Portability.
-  Start up in milliseconds.
-  Performance.
-  Multiple containers.
-  Keep your workspace clean.

**<a name="container">
Container
</a>**
 - Runnable instance of an image.
 - You can start, stop, or remove.

**<a name="image">
Image
</a>**

- Template with instructions for creating docker container.
- You may build your image.

**<a name="registry">
Registry
</a>**

- Stores docker images.
- Docker hub is the default public registry.

**<a name="client">
Docker Client
</a>**
  - is the primary way that many Docker users interact with Docker.

**<a name="daemon">
Docker Daemon
</a>**

- listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes.

**<a name="architecture">
Docker Architecture
</a>**

![Docker Architecture](architecture-docker.jpg)


**<a name="commands">
Docker Commands
</a>**

- Docker version
  
  - `docker --version`
  - `docker -v`

- List all containers
  
  - `docker container ls`  **List currently running containers**
  - `docker container ls -a` **List all docker containers (running and stopped)**
  - `docker ps`
  - `docker ps -a`

- Remove a stopped container
  - `docker container rm <container_name>`
  - `docker rm <container_name>`
    
- Delete all containers (only if stopped)
    - `docker rm $(docker ps -a -q)`  
- Start or stop an existing container
   - `docker start|stop <container_name> (or <container-id>)`

- Stop all running containers
 - `docker stop $(docker ps -a -q)`

- Create and run a container from an image, with a custom name
  - `docker run --name <container_name> <image_name>`
  
   - If the image doesn't exist on your local machine, the docker daemon get it from the 
     docker hub (registry).
   - If you don't specify the tag of the image, it pulled the latest version.
  
- Run a container in the background
  - `docker run -d <image_name>`  
  
- Run a container with and publish a container’s port(s) to the host
   - `docker run -p <host_port>:<container_port> <image_name>`
  
- List all images
    - `docker images`
  
- Delete an Image
   - `docker image rm <image_name>`
   - `docker rmi <image_name>`

- Delete all existing images
 - `docker image rm $(docker images -a -q)`

- Remove all unused images
  - `docker image prune`

- Pull an image from a Docker Hub
  - `docker pull <image_name>`

- Inspect a running container
  - `docker inspect <container_name> (or <container_id>)`

- Fetch the logs of a container:
  - `docker logs <container_name>`

- Display a live stream of container(s) resource usage statistics
  - `docker stats <container_name> (or <container_id>)`
  - `docker stats` ** all containers**

- Display system-wide information memory, cpu, version, images, containers count
  - `docker info`

- Run Container with full example
  `docker run -d -p 80:80 --name n1 --network=networkName -v=pathLocal:/pathContainer ngnix`

- Interact with container
  - `docker exec -it <container_name> (or <container_id>) command`
  - `docker exec -it n1 bash`


**<a name="dockerfile">
DockerFile
</a>**

- Is text document can build images automatically by reading the instructions from a Dockerfile.

  ![DockerFile](Dokcerfile.png)

### Docker Instructions: 
  - A Dockerfile must begin with a FROM instruction.
  - add comment with `#`.
  - CMD ["command", "argument"].
  - ENTRYPOINT ["command", "argument"].
  - To build image with the Dockerfile, which it on the same path:
    - `docker build .`
    - `docker build --tag tagName .`


**<a name="dockercompose">
Docker Compose
</a>**

- Tool for running multiple containers with `docker-compose.yml` file on the **same host**.

- Is very useful to build your env as a one package.
  
  `docker-composer -v`

  - we consider the service as a container.
  - we use `docker-compose.yml` or `docker-compose.yaml` to build the env.

- Docker-compose Commands:
  - `docker-compose start`
  - `docker-compose stop`
  - `docker-compose pause`
  - `docker-compose unpause`
  - `docker-compose ps`
  - `docker-compose up`
  - `docker-compose down`


**<a name="dockerswarm">
Docker Swarm
</a>**
  - Container orchestration tool allows you to run & connect containers on multiple hosts.
    
**<a name="k8s">
Kubarnates
</a>**
- Container orchestration tool like docker swarm, but it is more popular and work with large scale.


**<a name="dockercommit">
Docker Commit
</a>**
- Convert running container to an image.

  `docker commit <container-name> new-name-img:v1`


----------------------------------------------------
## Additional
## Containers:
#### Listing containers (up & running)
- docker ps
- docker container ls
#### Listing containers (up & running ) & (stopped)
- docker ps --all
- docker container ls --all
#### Run container
- docker run nginx
#### Stop container
- docker container stop container_id
#### Kill container
- docker container kill container_id
#### Publishing port
- --publish <host port>:<container port>
- --p <host port>:<container port>
- docker run --p 8080:80 nginx
- visit [localhost:8080](#http://127.0.0.1:8080)
#### Detached Mode
- -d
- --detach
- docker run -d --p 8080:80 nginx
- visit [localhost:8080](#http://127.0.0.1:8080)
#### Naming or Renaming Containers
- --name
- docker run -d --p 8080:80 --name nginx-orcas nginx
- visit [nginx-orcas](#http://127.0.0.1:8080)
#### Renaming Containers
- docker container rename nginx-orcas nginx-orcas-2
#### Removing Containers
- docker container rm nginx-orcas-2
#### Creating Containers Without Running
- docker container create nginx
- docker container start container_id
#### Remove container after stopped
- docker run --rm -p 8080:80 nginx
#### Mount Containers
- --volume <local file system directory absolute path>:<container file system directory absolute path>
- -v <local file system directory absolute path>:<container file system directory absolute path>
___
# Images:
### Listing images:
- docker images
- docker image ls
### Removing image:
- docker image rm image_id
- docker rmi image_id
### Pulling images:
- docker image pull nginx
### To build an image using the Dockerfile
- docker build .
  - The daemon finds any file named Dockerfile within the context.
---
# Networks:
### Listing networks:
- docker network ls
### Listing networks:
- docker network ls
  #### bridge:
  - The default networking driver in Docker. This can be used when multiple containers are running in standard mode and needs to communicate with each other.
### Creating network:
- docker network create <network name>
### Attaching Containers to a Network:
- docker network connect <network identifier> <container identifier>
- --network <network identifier>
- docker container run --network orcas --rm alpine
### Detaching Containers from a Network:
- docker network disconnect <network identifier> <container identifier>
### Removing network:
- docker network rm <network identifier>
---
# Docker compose:
- Just like the Docker daemon uses a Dockerfile for building images, Docker Compose uses docker-compose.yaml file to read service definitions from.
- docker-compose up
- docker-compose --file docker-compose.yaml up --detach
- docker-compose ps //listing services
- docker-compose exec <service name> <command> // Executing Commands Inside a Running Service
- docker-compose down
- docker-compose logs <service name>

------------------------------------

- `docker-compose up -d`
  - create the path for mysql.
  - create the path for nginx and conf file.
  - create the path for php and conf file.
  - create the path for project.
  - download app and change .env files.
    with the host of mysql service name.
  - change permissions of storage path.
    - ` sudo chmod 777 -R storage/ `
  - exec for php service php artisan migrate.
  - **default.conf** file in **nginx** `fastcgi_pass php:9000;`
    **php** refer to the service name and its port 9000

#### All these ports of services
- nginx - :8070
- mysql - :3309
- php - :9000
- phpmyadmin - :8081