Docker is a platform for developing, shipping, and running applications in lightweight, portable containers. Containers encapsulate an application and its dependencies (libraries, frameworks, etc.), ensuring that the application runs consistently across different computing environments, whether it's on a developer's machine, a testing environment, or a production server.

#Installation Script:
https://github.com/bh-gaur/docker/blob/main/install.sh

## Architecture of Docker

Docker uses a client–server architecture. The Docker client talks to the Docker Daemon, which builds, runs, and manages containers. They communicate through a REST API via UNIX sockets or a network interface.

1. Docker is based on a client–server model.
2. The Docker client sends requests to the Docker Daemon.
3. The Docker Daemon handles container lifecycle tasks.
4. Communication happens over a REST API using sockets or networks.

![Docker Host Architecture](https://media.geeksforgeeks.org/wp-content/uploads/20251218122638607429/docker_host.webp)

![Docker Objects](https://media.geeksforgeeks.org/wp-content/uploads/20260206152754426458/docker_objects.webp)

## Images

An image is a read-only, inert template that contains the instructions for creating a Docker container. Think of it as a blueprint or a class in object-oriented programming.

- It's built from a Dockerfile, a simple text file defining the steps to assemble the image.
- Images are built in layers, where each instruction in the Dockerfile corresponds to a layer. This layered architecture makes builds and distribution incredibly efficient.

## Containers

A container is a runnable, live instance of an image. If an image is the blueprint, a container is the house built from that blueprint.

- You can create, start, stop, move, or delete containers using the Docker API or CLI.
- Each container is isolated from other containers and the host machine, having its own filesystem, networking, and process space.
- You can run multiple containers from the same image.

## Storage

Since a container's writable layer is ephemeral (data is lost when the container is deleted), Docker provides robust solutions for data persistence. Storage driver controls and manages the images and containers on our docker host.
