# Docker Volumes & Networking

## Task-1
<img width="1920" height="943" alt="image" src="https://github.com/user-attachments/assets/04ec34a7-09d3-406d-9c0a-6f28f661cfa7" />
<img width="1920" height="805" alt="image" src="https://github.com/user-attachments/assets/0012ab93-398e-44a9-8df2-ee460c57bed2" />
 Container filesystem is ephemeral.

 ## Task-2
```
docker volume create pg-data
```
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fd3163ef-ccc6-4099-9ce2-ace5e2bab021" />
<img width="1920" height="675" alt="image" src="https://github.com/user-attachments/assets/24645ed5-8910-446b-a51f-3825e6da6057" />

## Task -3
- rtvk@rtvk-ThinkPad-E14-Gen-4:~/SL Devops/Module -7/Day-32/website$ docker run -d --name my-website -p 8000:80 -v "$(pwd)":/usr/share/nginx/html/ nginx:alpine
(it wont work cos of the spcae in pwd)
- rtvk@rtvk-ThinkPad-E14-Gen-4:~/SL Devops/Module -7/Day-32/website$ docker run -d --name my-website -p 8000:80 -v "$(pwd)":/usr/share/nginx/html/ nginx:alpine
(it will work bcoz " ")

| Named Volume                     | Bind Mount                              |
| -------------------------------- | --------------------------------------- |
| Managed by Docker                | Uses a host folder                      |
| Docker decides storage location  | You decide the folder                   |
| Mainly for persistent data (DBs) | Mainly for development                  |
| Container changes persist        | Host and container share the same files |
 
```
Named Volume → Database/Data Persistence
Bind Mount → Live code or file sharing during development
```
#### Named Volume: volume-name : container-path
- Left side is a Docker-managed volume.
- It stores data persistently, but Docker manages where it is stored.
- Mainly used for databases (PostgreSQL, MySQL, MongoDB).

#### Bind Mount: host-path : container-path

-  Left side is a host directory (your local folder).
- Changes on the host are reflected immediately in the container ("live").
-  Mainly used during development.
  
## Task -4
- docker network ls
- docker network inspect bridge

- docker run -dit --name c1 alpine sh /docker run -dit --name c2 alpine sh
    - apk add iputils


| Test         | Default Bridge |
| ------------ | -------------- |
| Ping by name | ❌ No           |
| Ping by IP   | ✅ Yes          |

* **Default `bridge`** → No automatic container name resolution.
* **User-defined bridge** → Supports container name resolution (DNS). This is what you'll use next.

## Task -5
- docker network create --driver bridge my-app-net / docker network create my-app-net (bridge is default)
- docker run -dit --name net1 --network my-app-net alpine sh / docker run -dit --name net2 --network my-app-net alpine sh
- docker exec -it net1 sh >> apk add iputils / docker exec -it net2 sh >> apk add iputils
- from net >> ping net2
Default bridge ❌ No built-in DNS.
Custom bridge ✅ Built-in Docker DNS

## Task - 6
```
docker network create my-app-net
docker volume create pg-data
docker run -d --name postgress-db --network  my-app-net -v pg-data:/var/lib/postgressql/data -e POSTGRES_PASSWORD=admin postgres:16-alpine
docker run -dit --name app --network my-app-net alpine sh
  docker exec -it app sh
  apk add iputils
  ping postgres-db
```
Docker's custom network provides built-in DNS.


# Summary 

## Docker Bridge Networks

Docker has **2 types of bridge networks**:

## 1. Default Bridge Network (`bridge`)

- Created automatically by Docker.
- Containers join this network if `--network` is not specified.
- ✅ Communication by IP address.
- ❌ Communication by container name (no built-in Docker DNS).

Example:

```bash
docker run -dit --name c1 alpine sh
docker run -dit --name c2 alpine sh
