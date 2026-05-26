# Docker

## Whats  the diff between image,container and engine?
- Image → A package/template that contains application code and dependencies.
- Container → A running instance of that image.
- Engine → The platform/software that creates and manages containers
- Docker Compose: A tool for defining and running multi-container applications using a YAML file.
- Dockerfile: A text document containing all the commands a user could call on the command line to assemble an image.

## Diff btw copy vs add
- COPY → simply copies files/folders from local system to Docker image.
- ADD → can do everything COPY does + extra features.

Extra features of ADD:

Can extract .tar files automatically
Can download files from URLs

## Diff btw cmd vs entrypoint vs run
- RUN → Used while building the Docker image.
- CMD → Default command that runs when container starts.  Provides a default command/arguments that can be overridden.
- ENTRYPOINT → Main command that always runs in the container. Defines the main executable of the container and is usually not overridden.

## How to reduce the size of docker image?
- Use lightweight base images
- Use .dockerignore
- Combine RUN commands (Minimise layers)
```
RUN apt update && apt install -y nginx && apt clean
```
## Why and when to use Docker?
- Why: It ensures consistency across different environments (Development, Staging, Production) by packaging the application with all its dependencies.
- When: Use it when you need to simplify deployment, scale applications quickly, or isolate microservices to avoid "it works on my machine" issues.

## Explain the Docker components and how they interact with each other.
- Docker Client: The primary way users interact with Docker (via CLI).
- Docker Host (Daemon): The background service managing containers, images, and networks.
- Docker Registry: A repository (like Docker Hub) where images are stored and pulled from.
- Interaction: The Client sends commands (e.g., docker run) to the Daemon, which pulls the necessary Image from the Registry to create and run a Container.

# Hypervisor vs Docker
| Feature     | Docker (Containers)       | Hypervisor / VMs                      |
| ----------- | ------------------------- | ------------------------------------- |
| OS          | Shares host OS kernel     | Each VM has its own guest OS          |
| Speed       | Starts in seconds         | Starts in minutes                     |
| Resources   | Lightweight, less RAM/CPU | Heavy, more resource usage            |
| Size        | Small image size          | Large VM size                         |
| Performance | Near-native performance   | Slightly slower due to virtualization |
| Isolation   | Process-level isolation   | Full OS-level isolation               |
| Portability | Easily portable           | Less portable                         |
| Example     | Docker Container          | VMware VM, VirtualBox VM              |

## What is a Docker namespace?
> Docker namespace is a Linux feature that provides isolation to containers.
> It separates processes, network, users, and filesystems so each container works independently.

## How to implement CI/CD in Docker?
> We can implement CI/CD using tools like Jenkins or GitHub Actions.

Basic flow:
1. Developer pushes code
2. CI tool builds Docker image
3. Run tests
4. Push image to registry
5. Deploy container automatically

---

### 11. Will data be lost when container exits?
> Yes, container data can be lost after deletion because containers are ephemeral.
> To persist data, we use Docker volumes or bind mounts.

### 12. What is Docker Swarm?
> Docker Swarm is Docker’s native container orchestration tool.
> It helps manage multiple containers across multiple servers.

Features:
* Load balancing
* Scaling
* High availability

# 13. Important Docker Commands

### View running containers

```bash id="c8x1kp"
docker ps
```

### Run container with specific name

```bash id="g4m2zd"
docker run --name mycontainer nginx
```

### Export a Docker container

```bash id="r7v9lt"
docker export container_id > backup.tar
```

### Import existing Docker image

```bash id="u2n6qe"
docker import backup.tar myimage
```

### Delete a container

```bash id="w9p3as"
docker rm container_id
```

### Remove stopped containers, unused networks, cache, dangling images

```bash id="k5j8vn"
docker system prune -a
```

---

# Common Docker Commands Used Daily

```bash id="e3q7rm"
docker images
docker ps -a
docker build -t myapp .
docker pull nginx
docker push myimage
docker logs container_id
docker exec -it container_id bash
docker stop container_id
docker start container_id
docker rm container_id
docker rmi image_id
```


