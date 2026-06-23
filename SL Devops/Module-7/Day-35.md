Multi-Stage Builds & Docker Hub

##### Multi-stage builds are how real teams ship small, secure images. Docker Hub is how you distribute them. Both are interview favourites.

## Task - 1
### Single stage

```
FROM node:22-alpine

WORKDIR /app

COPY . .

CMD ["npm", "start"]
```
163 -> mb

### Task - 2

```
# Stage 1 - Build
FROM node:22-alpine AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# Stage 2 - Runtime
FROM node:22-alpine

WORKDIR /app

COPY --from=builder /app .

CMD ["npm", "start"]

```
### Single-Stage Build
- Build tools and runtime are in the same image.
- Final image contains unnecessary files.
- Larger image size.

### Multi-Stage Build
- Stage 1: Build the application.
- Stage 2: Copy only the required application files into a new image.

### Why is the multi-stage image smaller?

- Build dependencies are not included.
- Temporary files are discarded.
- Source files that aren't needed can be omitted.
- Only the runtime environment and application are included.
- Smaller images download faster.
- Less storage usage.
- Reduced attack surface because fewer packages are present.

### Task - 3
- docker login
- docker tag hello-node:multi rtvk/hello-node:v1 (hello-node (repo name) : multi (tag))
- docker push rtvk/hello-node:v1 (hello-node (repo name) : v1 (tag))

### Task - 4
<img width="1561" height="680" alt="image" src="https://github.com/user-attachments/assets/76d49f51-1e75-4448-a195-6a9586e104c8" />

| Tag      | Version                             |
| -------- | ----------------------------------- |
| `v1`     | First release                       |
| `v2`     | Second release                      |
| `latest` | Points to the newest stable release |

### Task -5
```
FROM node:22-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install && \
    addgroup -S appgroup && \
    adduser -S appuser -G appgroup

COPY . .

USER appuser

CMD ["npm", "start"]
```

# Docker Image Best Practices

## 1. Use a Minimal Base Image

Good:

```dockerfile
FROM node:22-alpine
```

Avoid:

```dockerfile
FROM ubuntu
FROM node:latest
```

Smaller images:
- Download faster
- Use less storage
- Have fewer vulnerabilities

---

## 2. Don't Run as Root

```dockerfile
RUN addgroup -S appgroup && \
    adduser -S appuser -G appgroup

USER appuser
```

Running as a non-root user improves container security.

---

## 3. Combine RUN Commands

Good:

```dockerfile
RUN npm install && \
    addgroup -S appgroup && \
    adduser -S appuser -G appgroup
```

Benefits:
- Fewer image layers
- Slightly smaller image
- Better build performance

---

## 4. Use Specific Image Tags

Good:

```dockerfile
FROM node:22-alpine
```

Bad:

```dockerfile
FROM node:latest
```

Specific tags ensure consistent and reproducible builds.

---

## Check Image Size

```bash
docker images
```

