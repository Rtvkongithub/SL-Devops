# Docker-compose

## Task -1
- sudo apt-get install docker-compose && docker --version

## Task - 2
- nano docker-compose
```
services:
  nginx:
    image: nginx:alpine
    container_name: my-web 
    ports:
      - "8087:80
```
- docker compose up -d
- docker compose down

## Task - 3

```
services:
  db:
    image: mysql:8.0
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root123
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wpuser
      MYSQL_PASSWORD: wp123
    volumes:
      - mysql-data:/var/lib/mysql

  wordpress:
    image: wordpress:latest
    restart: always
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wpuser
      WORDPRESS_DB_PASSWORD: wp123
      WORDPRESS_DB_NAME: wordpress
    depends_on:
      - db

volumes:
  mysql-data:
```

Task - 4
- docker compose up -d
- docker ps
- docker compose logs
- docker compose log <service_name>
- docker compose stop
- docker compose down
- docker rm up -d --build

Task - 5
- nano .env
```
MYSQL_ROOT_PASSWORD=root123
MYSQL_DATABASE=wordpress
MYSQL_USER=wpuser
MYSQL_PASSWORD=wp123
```
- nano docker-compose.yml
```
services:
  db:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: ${MYSQL_ROOT_PASSWORD}
      MYSQL_DATABASE: ${MYSQL_DATABASE}
      MYSQL_USER: ${MYSQL_USER}
      MYSQL_PASSWORD: ${MYSQL_PASSWORD}
```
- docker compose up -d
- docker exec -it <container_name> env
