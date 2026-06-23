
## Task -1
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/13aca15e-1792-4f22-81b4-f5a0d8ebd7e1" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6789a69d-624d-4575-8145-8ea4d1c59ff4" />

## Task - 2
<img width="817" height="677" alt="image" src="https://github.com/user-attachments/assets/9721d5fe-2b47-4503-9b5e-9e447ab11c89" />
Yes app wait for DB. Docker waits until the health check passes (healthy).

## Task - 3

<img width="1348" height="576" alt="image" src="https://github.com/user-attachments/assets/4c721af2-c868-4284-ac4f-58f6d5d00c25" />

### restart: always
- Restarts the container whenever it stops.
- Also restarts after Docker daemon or host reboot.
- Best for production services like databases, Redis, and web servers.

### restart: on-failure
- Restarts only if the container exits with a non-zero exit code.
- Does not restart after a manual stop (`docker stop` or `docker kill`).
- Useful for batch jobs or applications that should retry after crashes.

| Policy           |     Restarts after crash    | Restarts after manual `docker stop` |                                                 Restarts after Docker/host reboot                                                 |
| ---------------- | :-------------------------: | :---------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------: |
| `no`             |              ❌              |                  ❌                  |                                                                 ❌                                                                 |
| `always`         |              ✅              |     ✅ (when Docker starts again)    |                                                                 ✅                                                                 |
| `unless-stopped` |              ✅              |                  ❌                  |                                               ✅ (only if it wasn't manually stopped)                                              |
| `on-failure`     | ✅ (non-zero exit code only) |                  ❌                  | Depends—only if it had failed and Docker's restart logic applies; it does not restart simply because the daemon or host rebooted. |


## Task - 4

- Make a docker-file
```
services:
  web:
    build: .
    ports:
      - "5000:5000"

  db:
    image: postgres:16-alpine
    environment:
      POSTGRES_PASSWORD: admin

  redis:
    image: redis:alpine
```

## Task -5
```
services:
  web:
    build: .
    ports:
      - "5000:5000"
    depends_on:
      db:
        condition: service_healthy
    networks:
      - app-network
    labels:
      app: flask-app
      env: dev

  db:
    image: postgres:16-alpine
    restart: always
    environment:
      POSTGRES_PASSWORD: admin
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres"]
      interval: 5s
      timeout: 5s
      retries: 5
    volumes:
      - postgres-data:/var/lib/postgresql/data
    networks:
      - app-network
    labels:
      app: postgres-db
      env: dev

  redis:
    image: redis:alpine
    networks:
      - app-network
    labels:
      app: redis-cache
      env: dev

networks:
  app-network:
    driver: bridge

volumes:
  postgres-data:
```

## Task - 6
# Docker Compose Scaling

## Scale a service

```bash
docker compose up -d --scale web=3
```

## What happens?

If the service has:

```yaml
ports:
  - "5000:5000"
```

only one container can bind to host port 5000.

The other replicas fail with:

```
port is already allocated
```

## Why doesn't simple scaling work?

- A host port can only be mapped to one container.
- Multiple containers cannot all use `5000:5000`.

## How is scaling done in production?

- Remove host port mappings from application containers.
- Use `expose` for internal communication.
- Put a load balancer/reverse proxy (Nginx, Traefik, HAProxy, etc.) in front of the replicas.

## Interview Point

- `docker compose --scale` creates multiple container replicas.
- Port mapping prevents multiple replicas from using the same host port.
- A reverse proxy or load balancer is required to distribute traffic across the replicas.
