Introduction

I recently completed a Docker course and have compiled my learnings in this repository. This includes fundamental concepts, benefits, commands, and practical implementations that I explored during the course. Below are the key topics I covered, which provide a structured overview of Docker's role in modern software development.

Table of Contents

Benefits of Docker

Development Process with Containers

Difference Between Docker and Virtual Machine

Docker Images

Docker Containers

Docker Registry

Docker Hub

Docker Commands

Port Binding

Container Port vs Host Port

Private Docker Registry Examples

Registry vs Repository

Dockerfile

Node.js Application with Docker

Build Images

Benefits of Docker

Provides consistency across different environments (development, testing, production).

Reduces dependency conflicts and "works on my machine" issues.

Enables efficient resource utilization compared to traditional virtual machines.

Speeds up application deployment with containerization.

Supports microservices architecture with isolated containers.

Development Process with Containers

Developers write code and package it into a Docker container.

The container is tested in a local or shared development environment.

The tested container is pushed to a registry (e.g., Docker Hub, private registry).

CI/CD pipelines deploy the container to staging/production environments.

Difference Between Docker and Virtual Machine

Feature

Virtual Machine

Docker

Resource Usage

Heavy (requires full OS)

Lightweight (shares OS kernel)

Boot Time

Slow

Fast

Isolation

Full OS virtualization

Process-level isolation

Portability

Limited

High

Docker Images

A Docker image is a blueprint containing the application and dependencies.

Images are reusable and can be version-controlled.

Docker Containers

A container is a running instance of a Docker image.

Containers can be started, stopped, and removed without affecting the image.

Docker Registry

A storage and distribution system for Docker images.

Public registries include Docker Hub, AWS ECR, and Azure Container Registry.

Private registries can be hosted on a local or cloud server.

Docker Hub

The default public registry for Docker images.

Provides a vast collection of pre-built images.

Docker Commands

Pull an Image

docker pull ubuntu

Run a Container

docker run -it ubuntu bash

List Running Containers

docker ps

List All Containers

docker ps -a

Remove a Container

docker rm container_id

Port Binding

Allows external access to a containerized application.

Example:

docker run -p 8080:80 nginx

Container Port vs Host Port

Container Port: The port inside the container where the application runs.

Host Port: The port on the host machine mapped to the container port.

Example Mapping: 8080:80 → Host 8080 maps to Container 80.

Private Docker Registry Examples

Run a Private Registry

docker run -d -p 5000:5000 --name registry registry:2

Push an Image to a Private Registry

docker tag my-app localhost:5000/my-app
docker push localhost:5000/my-app

Registry vs Repository

Registry: A storage location for Docker images (e.g., Docker Hub, private registry).

Repository: A collection of different versions of an image inside a registry.

Dockerfile

A Dockerfile defines how to build a custom image.
Example for a Node.js application:

FROM node:14
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "app.js"]

Node.js Application with Docker

Build the Image

docker build -t my-node-app .

Run the Container

docker run -p 3000:3000 my-node-app

Build Images

Use the docker build command to create an image from a Dockerfile.

Example:
