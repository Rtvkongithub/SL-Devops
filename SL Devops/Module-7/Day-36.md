# Docker Challenge Project

## Project

Node.js Express + MongoDB application

### Project Structure

```
docker-challenge/
├── app.js
├── package.json
├── Dockerfile
├── docker-compose.yml
├── .dockerignore
├── .env
└── README.md
```

---

# Task 1: Create the Application

## app.js

```
const express = require("express");
const mongoose = require("mongoose");

const app = express();

mongoose
  .connect(process.env.MONGO_URI)
  .then(() => console.log("MongoDB Connected"))
  .catch(err => console.log(err));

app.get("/", (req, res) => {
  res.send("Hello Docker Challenge!");
});

app.listen(3000, () => {
  console.log("Server running on port 3000");
});
```

## package.json

```
{
  "name": "docker-challenge",
  "version": "1.0.0",
  "scripts": {
    "start": "node app.js"
  },
  "dependencies": {
    "express": "^5.1.0",
    "mongoose": "^8.0.0"
  }
}
```

Install dependencies

```
npm install
```

---

# Task 2: Dockerfile

```
FROM node:22-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install && \
    addgroup -S appgroup && \
    adduser -S appuser -G appgroup

COPY . .

USER appuser

EXPOSE 3000

CMD ["npm","start"]
```

## .dockerignore

```
node_modules
.git
.env
Dockerfile
README.md
```

## Build Image

```
docker build -t docker-challenge:v1 .
```

## Run

```
docker run -p 3000:3000 docker-challenge:v1
```

---

# Task 3: Docker Compose

## docker-compose.yml

```
services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      MONGO_URI: ${MONGO_URI}
    depends_on:
      mongo:
        condition: service_healthy
    networks:
      - app-network

  mongo:
    image: mongo:8.0
    volumes:
      - mongo-data:/data/db
    networks:
      - app-network
    healthcheck:
      test: ["CMD", "mongosh", "--eval", "db.adminCommand('ping')"]
      interval: 10s
      timeout: 5s
      retries: 5

networks:
  app-network:

volumes:
  mongo-data:
```

## .env

```
MONGO_URI=mongodb://mongo:27017/dockerdb
```

Run

```bash
docker compose up -d --build
```

Stop

```bash
docker compose down
```

---

# Task 4: Ship It

## Tag Image

```
docker tag docker-challenge:v1 rtvk/docker-challenge:v1
```
<dockerhub-username>/<repository>:<tag>

Without tagging, if you try:
docker push docker-challenge:v1
Docker doesn't know which Docker Hub account or repository to push to.

## Push

```
docker push rtvk/docker-challenge:v1
```

## Docker Hub Link

```
https://hub.docker.com/r/rtvk/docker-challenge
```

---

# README.md

````
# Docker Challenge

## Description

Simple Node.js Express application with MongoDB using Docker Compose.

## Run

docker compose up -d --build

## Stop

docker compose down

## Environment Variable

MONGO_URI=mongodb://mongo:27017/dockerdb

Application URL

http://localhost:3000
