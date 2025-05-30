# Docker Commands Cheat Sheet
## Essential Commands Quick Reference
```bash
# Images
docker pull <image>         # Download image
docker images               # List images
docker rmi <image>          # Remove image

# Containers
docker run <image>          # Create and start container
docker ps                   # List running containers
docker ps -a                # List all containers
docker stop <container>     # Stop container
docker start <container>    # Start container
docker rm <container>       # Remove container

# Interaction
docker exec -it <container> bash    # Interactive shell
docker logs <container>             # View logs
docker cp <src> <dest>              # Copy files

# Cleanup
docker system prune        # Remove unused resources
docker container prune     # Remove stopped containers
docker image prune         # Remove unused images
```

## Useful Flags
```bash
-d          # Run in background (detached)
-it         # Interactive with terminal
-p          # Port mapping (host:container)
-v          # Volume mounting (host:container)
-e          # Environment variable
--name      # Container name
--rm        # Remove container when it stops
-f          # Force (for remove operations)
```

# Essential Commands
Docker commands follow this pattern:
```bash
docker [OPTIONS] COMMAND [ARG...]
```

## Image Management Commands
### Pull images from docker hub
```bash
# Pull the latest version of an image
docker pull nginx
docker pull ubuntu
docker pull node

# Pull a specific version (tag)
docker pull nginx:1.21
docker pull node:18-alpine
docker pull mysql:8.0
```
### List images
```bash
# List all images on your system
docker images

# Alternative command
docker image ls

# Show image IDs only
docker images -q
```

### Remove images
```bash
# Remove a specific image
docker rmi nginx
docker rmi nginx:1.21

# Remove image by ID
docker rmi 4bb46517cac3

# Remove multiple images
docker rmi nginx ubuntu node

# Remove all unused images
docker image prune

# Remove all images (careful!)
docker rmi $(docker images -q)
```

## Container Lifecycle Commands
### Run Container
```bash
# Basic run command
docker run hello-world

# Run in background (detached mode)
docker run -d nginx

# Run with custom name
docker run --name my-nginx nginx

# Run interactively
docker run -it ubuntu bash

# Run with port mapping
docker run -d -p 8080:80 nginx

# Run with environment variables
docker run -e MYSQL_ROOT_PASSWORD=mypassword mysql

# Run with volume mounting
docker run -d -p 8080:80 -v /host/path:/container/path nginx
```

### Start, stop, restart containers
```bash
# Stop a running container
docker stop container_name_or_id
docker stop my-nginx

# Stop multiple containers
docker stop nginx mysql redis

# Start a stopped container
docker start my-nginx

# Restart a container
docker restart my-nginx

# Stop all running containers
docker stop $(docker ps -q)
```

### Remove container
```bash
# Remove a stopped container
docker rm my-nginx

# Remove multiple containers
docker rm container1 container2

# Remove a running container (force)
docker rm -f my-nginx

# Remove all stopped containers
docker container prune

# Remove all containers (running and stopped)
docker rm -f $(docker ps -aq)
```

## Information and Monitoring Commands
### List containers
```bash
# List running containers
docker ps

# List all containers (running and stopped)
docker ps -a

# List container IDs only
docker ps -q

# List containers with specific format
docker ps --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"
```

### Container details
```bash
# Get detailed information about a container
docker inspect my-nginx

# Get specific information (using Go templates)
docker inspect --format='{{.NetworkSettings.IPAddress}}' my-nginx

# View container logs
docker logs my-nginx

# Follow logs in real-time
docker logs -f my-nginx

# View recent logs
docker logs --tail 50 my-nginx

# View logs with timestamps
docker logs -t my-nginx
```

### System information
```bash
# Show Docker system information
docker info

# Show Docker version
docker version

# Show disk usage
docker system df

# Show running processes in a container
docker top my-nginx
```

## Container Interaction Commands
### Execute commands in containers
```bash
# Execute a command in a running container
docker exec my-nginx ls /usr/share/nginx/html

# Start an interactive shell in a running container
docker exec -it my-nginx bash

# Execute as a specific user
docker exec -it --user root my-nginx bash

# Execute with environment variables
docker exec -e ENV_VAR=value my-nginx env
```

### Copy Files Between Host and Container
```bash
# Copy from host to container
docker cp /host/file.txt my-nginx:/usr/share/nginx/html/

# Copy from container to host
docker cp my-nginx:/usr/share/nginx/html/index.html /host/path/

# Copy directory
docker cp /host/directory my-nginx:/container/path/
```

## Cleanup Commands
### Remove un-used resources
```bash
# Remove all unused containers, networks, images, and build cache
docker system prune

# Remove everything including unused volumes
docker system prune -a --volumes

# Remove unused images only
docker image prune

# Remove stopped containers only
docker container prune

# Remove unused volumes only
docker volume prune

# Remove unused networks only
docker network prune
```

## Common Use Cases & Commands
### Development workflows
```bash
# Quick test environment
docker run -it --rm node:18 bash

# Run with current directory mounted
docker run -it --rm -v $(pwd):/app -w /app node:18 bash

# Run specific Node.js version for testing
docker run --rm -v $(pwd):/app -w /app node:16 npm test
```

### Debugging
```bash
# Check container resource usage
docker stats

# Check what's running inside container
docker exec container_name ps aux

# Check container network configuration
docker exec container_name ip addr show

# Check environment variables
docker exec container_name env
```