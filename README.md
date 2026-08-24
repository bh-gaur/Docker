# Docker Overview & Reference Guide

Docker is a platform for developing, shipping, and running applications in lightweight, portable containers. Containers encapsulate an application and its dependencies (libraries, frameworks, etc.), ensuring that the application runs consistently across different computing environments, whether it's on a developer's machine, a testing environment, or a production server.

## Installation

- [Installation Script (`install.sh`)](https://github.com/bh-gaur/docker/blob/main/install.sh)

---

## Architecture of Docker

Docker uses a client–server architecture. The Docker client talks to the Docker Daemon, which builds, runs, and manages containers. They communicate through a REST API via UNIX sockets or a network interface.

1. **Client-Server Model**: The Docker client sends commands (`docker run`, `docker build`) to the daemon.
2. **Docker Daemon (`dockerd`)**: Listens for API requests and manages Docker objects such as images, containers, networks, and volumes.
3. **Container Lifecycle**: The daemon handles building, running, and managing container lifecycles.
4. **REST API**: Communication happens over a REST API using sockets or network interfaces.

![Docker Host Architecture](https://media.geeksforgeeks.org/wp-content/uploads/20251218122638607429/docker_host.webp)

![Docker Objects](https://media.geeksforgeeks.org/wp-content/uploads/20260206152754426458/docker_objects.webp)

---

## Core Components

### 📦 Images

A Docker image is like a blueprint or a recipe for an application.

An image is a read-only, inert template that contains the instructions for creating a Docker container. Think of it as a blueprint or a class in object-oriented programming.

- **Dockerfile**: Built from a Dockerfile, a text file defining the steps to assemble the image.
- **Layered Architecture**: Built in read-only layers where each instruction creates a layer, making builds and distribution cached and efficient.

### 🚀 Containers

A container is a runnable, live instance of an image. If an image is the blueprint, a container is the house built from that blueprint.

- **Lifecycle**: Created, started, stopped, moved, or deleted using the Docker API or CLI.
- **Isolation**: Isolated from other containers and the host machine, having its own filesystem, networking, and process space.
- **Scalability**: Multiple containers can run simultaneously from the same image.

### 💾 Storage

Since a container's writable layer is ephemeral (data is lost when the container is deleted), Docker provides robust storage mechanisms managed by storage drivers:

- **Volumes**: Stored in a host filesystem area managed by Docker (`/var/lib/docker/volumes/`). Best for persistent data.
- **Bind Mounts**: Can be stored anywhere on the host system, giving containers access to host files or directories.
- **tmpfs**: Stored in host memory only, never written to the host filesystem.

### 🌐 Networking

Docker provides pluggable network drivers for container communication:

- **bridge**: Default network driver for standalone containers.
- **host**: Removes network isolation between container and host.
- **overlay**: Enables networking across multiple Docker daemons (Swarm).
- **none**: Disables networking for the container.

---

## ⚡ Quick CLI Reference

| Command                                      | Description                               |
| :------------------------------------------- | :---------------------------------------- |
| `docker build -t app:v1 .`                   | Build image from Dockerfile               |
| `docker run -d -p 8080:80 --name web app:v1` | Run container in background mapping ports |
| `docker ps -a`                               | List all containers                       |
| `docker logs -f <container_id>`              | Stream container logs                     |
| `docker exec -it <container_id> sh`          | Open interactive terminal in container    |
| `docker stop <container_id>`                 | Gracefully stop running container         |
| `docker rm <container_id>`                   | Remove a stopped container                |
| `docker rmi <image_id>`                      | Remove a local image                      |
