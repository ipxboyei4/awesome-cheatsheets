#!/usr/bin/env bash
# Docker Cheatsheet

# --- CONTAINER MANAGEMENT ---
# Run container
docker run -d --name container_name -p 8080:80 image_name

# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Stop / Start / Restart container
docker stop container_name
docker start container_name
docker restart container_name

# Remove container
docker rm container_name

# Force remove container
docker rm -f container_name

# Exec shell in container
docker exec -it container_name /bin/bash

# View logs
docker logs -f --tail 100 container_name

# --- IMAGE MANAGEMENT ---
# Build image
docker build -t image_name:tag .

# List images
docker images

# Remove image
docker rmi image_name

# Pull / Push image
docker pull image_name:tag
docker push image_name:tag

# --- CLEANUP ---
# Remove stopped containers
docker container prune

# Remove unused images
docker image prune -a

# Remove unused volumes
docker volume prune

# Remove unused networks
docker network prune

# Clean up everything unused (containers, networks, images, volumes)
docker system prune -a --volumes

# Filter cleanup by age (e.g., older than 24h)
docker system prune -a --filter "until=24h"