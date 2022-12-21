# Commands

## Build image from dockerhub

```bash
docker run -d -p 80:80 docker/getting-started
```

## Build image locally with dockerfile

```bash
docker build -t getting-started .
```

## Start the app

```bash
docker run -dp 3000:3000 getting-started
```

- *d* to detach
- *p* to bind port

## Update the app

### Change source code

### Remove existing container (GUI/cmd)

```bash
docker stop <the-container-id>
docker rm <the-container-id>
```

or

```bash
docker rm -f <the-container-id>
```

### Rebuild image, recreate app container

## Add image to docker hub

```bash
docker push docker/getting-started
```

## Add volumes for DB

```bash
docker volume create todo-db
```

## Add volume to container by mount binding

```bash
docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
```

### Recreating containers will now persist data in our app

### Check where Docker stores the voluem

```bash
docker volume inspect todo-db
```

## Create container with our app

```bash
docker run -dp 3000:3000 \
    -w /app -v "$(pwd):/app" \
    node:18-alpine \
    sh -c "yarn install && yarn run dev"
```

### Check logs

```bash
docker logs <container_id>
```

### Attach to container

```bash
docker exec -it <container_id> /bin/bash
```

## Create a network

```bash
docker network create todo-app
```

### Use with app

```bash
docker run -d \
    --network todo-app --network-alias mysql \
    -v todo-mysql-data:/var/lib/mysql \
    -e MYSQL_ROOT_PASSWORD=secret \
    -e MYSQL_DATABASE=todos \
    mysql:8.0
```

## Docker Compose

```bash
docker compose up -d
docker compose down
```

### Delete with volumes

```bash
docker compose down --volumes
```

### Check logs

```bash
docker compose logs -f
```
