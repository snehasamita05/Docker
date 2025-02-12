# Docker Course Learnings

I recently completed a Docker course and have compiled my learnings in this repository. This includes fundamental concepts, benefits, commands, and practical implementations that I explored during the course. Below are the key topics I covered, which provide a structured overview of Docker's role in modern software development.

## Table of Contents

1. [Benefits of Docker](#benefits-of-docker)
2. [Development Process with Containers](#development-process-with-containers)
3. [Difference Between Docker and Virtual Machine](#difference-between-docker-and-virtual-machine)
4. [Docker Images](#docker-images)
5. [Docker Containers](#docker-containers)
6. [Docker Registry](#docker-registry)
7. [Docker Hub](#docker-hub)
8. [Docker Commands](#docker-commands)
9. [Port Binding](#port-binding)
10. [Container Port vs Host Port](#container-port-vs-host-port)
11. [Private Docker Registry Examples](#private-docker-registry-examples)
12. [Registry vs Repository](#registry-vs-repository)
13. [Dockerfile](#dockerfile)
14. [Node.js Application with Docker](#nodejs-application-with-docker)
15. [Build Images](#build-images)

## Benefits of Docker

- Provides consistency across different environments (development, testing, production).
- Reduces dependency conflicts and "works on my machine" issues.
- Enables efficient resource utilization compared to traditional virtual machines.
- Speeds up application deployment with containerization.
- Supports microservices architecture with isolated containers.

## Development Process with Containers

1. Developers write code and package it into a Docker container.
2. The container is tested in a local or shared development environment.
3. The tested container is pushed to a registry (e.g., Docker Hub, private registry).
4. CI/CD pipelines deploy the container to staging/production environments.

## Difference Between Docker and Virtual Machine

| Feature              | Virtual Machine            | Docker                      |
|----------------------|----------------------------|-----------------------------|
| **Resource Usage**    | Heavy (requires full OS)   | Lightweight (shares OS kernel) |
| **Boot Time**         | Slow                       | Fast                        |
| **Isolation**         | Full OS virtualization      | Process-level isolation     |
| **Portability**       | Limited                    | High                        |

## Docker Images

A Docker image is a blueprint containing the application and dependencies.  
- Images are reusable and can be version-controlled.

## Docker Containers

A container is a running instance of a Docker image.  
- Containers can be started, stopped, and removed without affecting the image.

## Docker Registry

A storage and distribution system for Docker images.  
- Public registries include Docker Hub, AWS ECR, and Azure Container Registry.  
- Private registries can be hosted on a local or cloud server.

## Docker Hub

The default public registry for Docker images.  
- Provides a vast collection of pre-built images.

## Docker Commands

- **Pull an Image**  
  `docker pull ubuntu`
  
- **Run a Container**  
  `docker run -it ubuntu bash`
  
- **List Running Containers**  
  `docker ps`
  
- **List All Containers**  
  `docker ps -a`
  
- **Remove a Container**  
  `docker rm container_id`

## Port Binding

Allows external access to a containerized application.  
Example:  
`docker run -p 8080:80 nginx`

## Container Port vs Host Port

- **Container Port:** The port inside the container where the application runs.  
- **Host Port:** The port on the host machine mapped to the container port.  
Example Mapping: `8080:80` → Host 8080 maps to Container 80.

## Private Docker Registry Examples

- **Run a Private Registry**  
  `docker run -d -p 5000:5000 --name registry registry:2`
  
- **Push an Image to a Private Registry**  
  `docker tag my-app localhost:5000/my-app`  
  `docker push localhost:5000/my-app`

## Registry vs Repository

- **Registry:** A storage location for Docker images (e.g., Docker Hub, private registry).  
- **Repository:** A collection of different versions of an image inside a registry.

## Dockerfile

A Dockerfile defines how to build a custom image. Example for a Node.js application:

```dockerfile
FROM node:14
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "app.js"]



