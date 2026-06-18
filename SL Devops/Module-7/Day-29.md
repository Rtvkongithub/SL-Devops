## Task-1 

### 1. Container

-   A lightweight package containing the application, dependencies, and
    runtime.
-   Ensures the app runs the same everywhere.
-   Benefits: Portable, fast, lightweight, isolated.

### 2. Containers vs Virtual Machines

  Container               Virtual Machine
  ----------------------- ----------------------
  Shares host OS kernel   Has its own Guest OS
  Lightweight (MBs)       Heavy (GBs)
  Starts in seconds       Starts in minutes
  Low resource usage      High resource usage

### 3. Docker Architecture

**Components:** - **Docker Client** -- Runs commands (`docker run`,
`docker build`). - **Docker Daemon (`dockerd`)** -- Builds images and
manages containers. - **Docker Image** -- Read-only template. - **Docker
Container** -- Running instance of an image. - **Docker Registry** --
Stores images (e.g., Docker Hub).

### 4. Architecture Flow
```
 text
Docker Client
      |
      v
Docker Daemon
      |
+-----+----------------+
|                      |
v                      v
Images            Containers
      ^
      |
Docker Registry
```

## Task-2
- sudo apt install docker.io
- docker --version
- docker run hello-world
- sudo usermod -aG docker $USER

## Task-3
- docker run -d --name nginx-container -p 8080:80 nginx
- docker exec -it nginx-container bash
- docker ps
- docker ps -a
- docker rm <docker name>
- docker stop <docker name>

## Task -4
- docker run -d nginx
- docker run -d --name my-nginx nginx
- docker run -d --name my-nginx -p 80:8080 nginx / http://localhost:8080
- docker logs my-nginx / docker logs -f my-nginx
- docker exec -it my-nginx bash


