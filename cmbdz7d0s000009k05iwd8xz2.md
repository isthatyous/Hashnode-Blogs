---
title: "The Complete Docker Setup: Lightweight Builds, Secure Images, and Connected Services"
seoTitle: "Docker: Builds, Security & Service Connection"
seoDescription: "Explore Docker's architecture: lightweight builds, secure images, seamless connected services for modern software development"
datePublished: Sun Jun 01 2025 18:10:06 GMT+0000 (Coordinated Universal Time)
cuid: cmbdz7d0s000009k05iwd8xz2
slug: the-complete-docker-setup-lightweight-builds-secure-images-and-connected-services
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1748801035685/4d8106dc-c672-4421-abf4-b07a1941e763.png
tags: docker, developer, devops, twscommunity

---

In the rapidly evolving landscape of software development and deployment, Docker has emerged as a game-changer. Its containerization technology has revolutionized the way applications are built, shipped, and run. To grasp the true essence of Docker and harness its full potential, it’s crucial to delve into its architecture. In this comprehensive guide, we’ll explore Docker’s architecture, unraveling its various components and their interactions.

# What is Docker?

Before we dive into the intricacies of Docker’s architecture, let’s first understand what Docker is. Docker is an open-source platform that enables developers to package their applications and dependencies into lightweight containers. These containers encapsulate everything an application needs to run, including code, runtime, system tools, and libraries. Docker containers are portable, scalable, and consistent across different environments, making it easier to develop, deploy, and manage applications.

# Architecture Overview

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1748757312490/62d661c1-12e4-4e8c-a619-64854ad2ce2c.webp align="center")

**Docker Engine:**

* The Docker Engine is the heart of the Docker platform. It comprises two main components:
    
* Docker Daemon (`dockerd`): The Docker daemon runs on the host machine and is responsible for managing Docker objects, such as images, containers, networks, and volumes.It listens to API requests from the CLI or remote clients.
    
* Docker Client: The Docker client is a command-line interface (CLI) tool that allows users to interact with the Docker daemon through commands. Users can build, run, stop, and manage Docker containers using the Docker CLI.The Docker client sends your comands to the Docker Daemon using REST API calls.
    

# How Docker Components Communicate

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1748758647614/aeb4392b-d68b-4521-9308-82ae1cd74a43.png align="center")

* `Container d` is CNCF certified tool that run in the backlground of the docker uses Linux kernel to make containers. Container means processes of Linux (where our application is running).
    
* `Docker Deamon` run on `Container d`. It talks to `container d` to create containers.
    
* Now the question is how we talk to Docker Deamon
    
    1\. `Docker CLI|`  
    2\. `Docker Client (Docker Desktop)`
    
* Whole Architecture works with Docker Engine or also called Docker Application Container Engine.
    

# How to add user to the Docker Group

By default, Docker commands (like `docker run`) require `root` privileges because the Docker daemon (`dockerd`) runs as root.

If you try running Docker as a non-root user with command ( `docker run` ) it will give the permission error `Got permission denied while trying to connect to the Docker daemon socket...` you need to prefix sudo everytime. Add your user to the `docker group` this gives the user permission to interact with Docker without using `sudo`, by granting access to the Docker socket file:

```bash
# 1. Create the docker group (in case it doesn't exist)
sudo groupadd docker

# 2. Add your user to the group
sudo usermod -aG docker $USER

# 3. Restart your shell session (important!)
# You can either:
# - log out and log back in
# OR
# - run:
# This command will refresh the docker group 
newgrp docker
```

# How to make and run Docker Image Inside the Container

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1748798563151/3da57e1a-9b52-4d70-aff2-94000c5e603f.png align="center")

## How to write Dockerfile

```bash
# Base Image (OS)
FROM Python:3.9-slim

# Set working directory inside container
WORKDIR /app

# Install dependencies
RUN pip install requirements.txt

# Copy source code
COPY . .

# Expose the port the app will run on
EXPOSE 80

# Command to run the app
CMD ["run.py"] 
```

Let’s unpack this Dockerfile line-by-line:

* `FROM Python:3.9-slim` – [The official Python image](https://hub.docker.com/layers/library/python/3.9-slim/images/sha256-b370e60efdfcc5fcb0a080c0905bbcbeb1060db3ce07c3ea0e830b0d4a17f758) is selected as the base image. All the other statements apply on top of `python:3.9`.
    
* `WORKDIR /app` – The working directory is changed to `/app`. Subsequent statements which use relative paths, such as the `COPY` instructions immediately afterwards, will be resolved to `/app` inside the container.
    
* `RUN pip install requirements.txt` – This instruction executes inside the container’s filesystem, fetching your project’s dependencies.
    
* `COPY . .` – Your app’s source code is added to the container. It happens after the `RUN` instruction because your code will usually change more frequently than your dependencies. This order of operations allows more [optimal usage](https://docs.docker.com/build/cache) of Docker’s build cache.
    
* `ENTRYPOINT ["python"]` – The image’s [entrypoint](https://docs.docker.com/engine/reference/builder/#entrypoint) is set so the `node` binary is launched automatically when you create new containers with your image.
    
* `CMD ["run.py"]` – This instruction supplies the **default argument** to the entrypoint. In this example, it results in **Python executing** [`run.py`](http://run.py), which runs your application’s main [script.](http://script.How)
    
    ## How to write Multi stage Dockerfile with Distroless Image
    
    Get the distroless image from here: [Distroless Image](https://github.com/GoogleContainerTools/distroless)
    

```bash
# ========== Stage 1: Build Stage ==========
# Use a lightweight official Python image for building
FROM Python:3.9-slim AS builder

# Set working directory inside container
WORKDIR /app

# Copy the entire application source code into the container
COPY . .

# Install dependencies into a separate folder (not globally)
# This helps in creating a clean final image
RUN pip install requirements.txt --target=/app/deps

# ========== Stage 2: Final Runtime Image ==========
# Use a minimal base image for running the app (distroless/debian-based)
from gcr.io/python-3/debian12

# Set the working directory inside the final container
WORKDIR /app

# Copy only the installed dependencies from the builder stage
COPY --from=builder /app/deps /app/deps

# Copy the application source code from the builder stage
COPY --from=builder /app .

# Expose the port your app runs on
EXPOSE 80

# Set the default command to run your Python application
# Since this is a distroless image, ensure run.py uses shebang or invoke python explicitly
CMD ["run.py"] 
```

## How to push Image to the Docker hub

1. Go to Docker Hub settings → create PAT (Personal Access Token).
    
2. In CLI → enter the command `docker login` put the username as docker hub username and password as PAT.
    
3. Login success msg will be shown.  
    If you get logged in succesfully the you can push or pull the image to your Docker Hub.
    
      
    **3.1 Push Docker Image to Docker Hub**
    
    ```bash
    # Step 1: Build the docker image 
    # here dot represent the context to build the image mean where your dockerfile is
    docker build local_image_name .
    
    # Step 2: Tag your local image with your Docker Hub username
    docker tag local-image-name dockerhub-username/image-name:tag
    
    # Step 3: Push the image to Docker Hub
    docker push dockerhub-username/image-name:tag
    ```
    
    **3.2 Pull Docker Image from Docker Hub**
    
    ```bash
    # Pull the image using your Docker Hub username and image name
    docker pull dockerhub-username/image-name:tag
    ```
    

## Docker Networking

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1748774822908/6533bfc2-fbda-466c-b522-9601490e8aea.png align="center")

**Docker Network** is a virtual network that allows Docker containers to communicate with each other, and optionally with the host machine or the outside world (Internet).

Think of it like giving each container a private IP address inside a small, isolated network.When we create a container by default a network is created and container run on its isolated network. Both container have their own isolated network. Here Flask App container need to interact with the MySQL container, then both the container should have to be connected with the common network between them.

## Types of Network in Docker

1. **Bridge (default)** : Default for standalone containers (isolated virtual LAN). While running any container, we do port mapping, this port mapping is done using the bridge network.
    
2. **None** : (Complete Isolation). It doesn’t allow anyone to connect.
    
3. **Host** : Normally, Docker gives each container its own network.But with the `host` network, the container uses your computer’s (host’s) network directly.
    
4. **User defined Bridge** : Network created by the User.
    
5. **overlay** : For multi-host communication (Docker Swarm, etc).
    
6. **macvlan** : Assigns MAC addresses, connects containers to physical network like real devices.  
    
    ```bash
    # Create a new custom Docker network
    docker network create network_name
    
    #List all Docker networks available on your system
    docker network ls
    
    # Run the docker container in that network
    docker run -d -p 80:80 --network network_name container1_name
    
    # Run the docker container in that network
    docker run -d -p 3306:3306 --network network_name container2_name
    ```
    

## Docker Volumes

A **Docker volume** is a special folder on your host system where Docker stores data from inside a container. By default, any data inside a Docker container is lost when the container stops or is deleted.  
Volumes keep your data safe and available, even if the container is removed. Multiple containers can access the same volume to share logs, access shared config files, store databases.Volumes are stored outside the container, so you can Easily back them up,Move them across environments.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1748797916933/b6d43534-7982-49a9-8ffc-66b1518424ec.png align="center")

```bash
# Create a volume
docker volume create mysql-data

# List all volumes
docker volume ls     

# Get details
docker volume inspect mysql-data

# To run MYSQL container we need its ROOT_PASS as Environment 
docker run -d \
  --name mysql-container \
  -e MYSQL_ROOT_PASSWORD=rootpass \
  -v mysql-data:/var/lib/mysql \  # volume mount
  -p 3306:3306 \
  mysql:latest

```

## Docker Compose file

`docker-compose.yml`

```bash
version: '3.9'

services:
  mysql:      
    image: mysql:8.0
    container_name: mysql-container
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: rootpass
      MYSQL_DATABASE: flaskdb
      MYSQL_USER: flaskuser
      MYSQL_PASSWORD: flaskpass
    volumes:
      - mysql-data:/var/lib/mysql   
    networks:
      - flasknet
    ports:
      - "3306:3306"

  flask:
    build: ./flask-app
    container_name: flask-app
    restart: always
    environment:
      DB_HOST: mysql
      DB_NAME: flaskdb
      DB_USER: flaskuser
      DB_PASSWORD: flaskpass
    ports:
      - "80:80"
    depends_on:
      - mysql
    networks:
      - flasknet

volumes:
  mysql-data:

networks:
  flasknet:
```

```bash
# Starts all services defined in docker-compose.yml
docker-compose up

# Stops and removes all containers, networks, and volumes created by docker-compose up
docker-compose down 
```