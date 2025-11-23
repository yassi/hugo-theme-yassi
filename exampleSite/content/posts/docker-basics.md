+++
title = "Docker Fundamentals for Developers"
date = 2024-03-05
summary = "Get started with Docker containerization and streamline your development workflow"
tags = ["docker", "containers", "devops"]
categories = ["DevOps"]
+++

Docker has become essential for modern development. Let's understand the fundamentals.

## What is Docker?

Docker packages applications and their dependencies into containers—lightweight, portable units that run consistently anywhere.

## Core Concepts

### Images

Templates for containers:

```bash
# Pull an image
docker pull node:18-alpine

# List images
docker images

# Build from Dockerfile
docker build -t myapp:1.0 .
```

### Containers

Running instances of images:

```bash
# Run a container
docker run -d -p 3000:3000 myapp:1.0

# List running containers
docker ps

# Stop a container
docker stop container-id

# Remove a container
docker rm container-id
```

### Dockerfile

Define your image:

```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

## Common Commands

```bash
# Build image
docker build -t myapp .

# Run container
docker run -p 3000:3000 myapp

# Run with volume
docker run -v $(pwd):/app myapp

# Run with environment variables
docker run -e NODE_ENV=production myapp

# Execute command in running container
docker exec -it container-id sh

# View logs
docker logs container-id

# View logs in real-time
docker logs -f container-id
```

## Docker Compose

Manage multi-container applications:

```yaml
# docker-compose.yml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/app
    environment:
      - NODE_ENV=development
    depends_on:
      - db
  
  db:
    image: postgres:15
    environment:
      - POSTGRES_PASSWORD=secret
    volumes:
      - db-data:/var/lib/postgresql/data

volumes:
  db-data:
```

Run with:
```bash
docker-compose up
docker-compose down
```

## Best Practices

### Optimize Images

```dockerfile
# Use specific versions
FROM node:18-alpine

# Combine RUN commands
RUN apk add --no-cache git && \
    npm install -g pnpm

# Use .dockerignore
# Add: node_modules, .git, *.md
```

### Security

- Don't run as root
- Use official base images
- Scan for vulnerabilities
- Keep images updated
- Use secrets management

### Development vs Production

```dockerfile
# Development
FROM node:18-alpine
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "run", "dev"]

# Production
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
CMD ["npm", "start"]
```

## Debugging

```bash
# Interactive shell
docker run -it myapp sh

# Inspect container
docker inspect container-id

# View resource usage
docker stats

# Check logs
docker logs --tail 100 container-id
```

Docker simplifies development, testing, and deployment. Start with these basics and gradually explore advanced features like networking, volumes, and orchestration.
