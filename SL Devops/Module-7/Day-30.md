## Task - 1 
- docker pull nginx/ ubuntu/ alpine
- docker images
- alpine is the smaller
- docker inspect alpine
- docker rmi nginx

## Task -2
<img width="1627" height="616" alt="image" src="https://github.com/user-attachments/assets/fb64bf3b-7155-465b-b8df-a8e83e5fdb3d" />
Docker uses layers to make images smaller, reusable, faster to build, and faster to download.

## Task - 3
- docker create --name my-nginx nginx
- docker start my-nginx
- docker pause my-nginx
- docker unpause my-nginx
- docker stop my-nginx
- docker restart my-nginx
- docker kill my-nginx
- docker rm my-nginx

docker kill work only on runnning container

## Task - 4
- docker run -d --name my-nginx nginx
- docker logs my-nginx
- docker logs -f my-nginx
- docker exec -it my-nginx bash
- docker exec my-nginx ls /
- docker inspect my-nginx

## Task -4
- docker stop $(docker ps -q)
#### -q = quite, container id kaanikkum / $() = parenthesis first 
- docker container prune
- docker image prune / docker image prune -a (all unused img)
- docker system df
