## Task - 1
- mkdir my-first-image
    - nano Dockerfile
<img width="1458" height="222" alt="image" src="https://github.com/user-attachments/assets/812dc006-0c95-4990-b574-476840d205d3" />

- docker build -t my-ubuntu:v1 .
- docker run --name (container name) (image name) / (no use of detatched mode cos it will get exit asap)
- docker exec -it (container name) bash / exec only works in running container (exec/run)

## Task - 2
<img width="1458" height="597" alt="image" src="https://github.com/user-attachments/assets/95c703d3-49b0-45c0-9f62-0f3cae10a9f6" />

## Task - 3
### CMD
<img width="1910" height="453" alt="image" src="https://github.com/user-attachments/assets/3691e27e-8beb-4bb5-be95-c1dcb82014cd" />

### Entrypoint
<img width="1916" height="621" alt="image" src="https://github.com/user-attachments/assets/ed4a0966-beff-4e50-9ec2-7a70863c32af" />

# CMD vs ENTRYPOINT

| CMD                                                  | ENTRYPOINT                                           |
| ---------------------------------------------------- | ---------------------------------------------------- |
| Sets the default command.                            | Sets the main executable.                            |
| Can be overridden by `docker run <image> <command>`. | Cannot be replaced easily; arguments are appended.   |
| Custom command **replaces** the CMD.                 | Custom arguments are **appended** to the ENTRYPOINT. |

### Example

**CMD**

```dockerfile
FROM ubuntu
CMD ["echo", "hello"]
```

```bash
docker run cmd-demo
# Output: hello

docker run cmd-demo ls
# Executes: ls
```

**ENTRYPOINT**

```dockerfile
FROM ubuntu
ENTRYPOINT ["echo"]
```

```bash
docker run entry-demo
# Output: (blank line)

docker run entry-demo hello world
# Executes: echo hello world
# Output: hello world
```
## Task - 4

<img width="968" height="210" alt="image" src="https://github.com/user-attachments/assets/96aec6d6-5ebb-49fa-b2b7-59e31f663ee0" />
<img width="998" height="328" alt="image" src="https://github.com/user-attachments/assets/7af5b6ea-529e-4f59-aba8-13239655f823" />
```
docker build -t my-website:v1 .
docker run -d --name website -p 8000:80 my-website:v1 
```

## Task - 5
<img width="1138" height="222" alt="image" src="https://github.com/user-attachments/assets/8f1470eb-fd57-4904-b00b-e90cf9affc41" />
<img width="1138" height="375" alt="image" src="https://github.com/user-attachments/assets/742bc06c-2189-4e54-b57f-96f7a099781b" />

## Task - 6
<img width="1920" height="943" alt="image" src="https://github.com/user-attachments/assets/639e4b5b-5dbf-4415-b349-0a364bf2b370" />

