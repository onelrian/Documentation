---
layout: page
title: Docker Commands & Container Management
---

# Docker Commands & Container Management

## Basic Docker Operations

### Container Lifecycle
```bash
# Run containers
docker run image                    # Run container from image
docker run -d image                 # Run in detached mode
docker run -it image bash           # Interactive with terminal
docker run --name mycontainer image # Named container
docker run -p 8080:80 image         # Port mapping (host:container)
docker run -v /host:/container image # Volume mounting
docker run --rm image               # Auto-remove when stopped
docker run -e VAR=value image       # Environment variable

# Container management
docker ps                           # List running containers
docker ps -a                        # List all containers
docker start container              # Start stopped container
docker stop container               # Stop running container
docker restart container            # Restart container
docker pause container              # Pause container
docker unpause container            # Unpause container
docker kill container               # Force kill container
docker rm container                 # Remove container
docker rm -f container              # Force remove running container
```

### Image Management
```bash
# Image operations
docker images                       # List local images
docker pull image:tag               # Download image
docker push image:tag               # Upload image to registry
docker build -t name:tag .          # Build image from Dockerfile
docker build --no-cache -t name .   # Build without cache
docker rmi image                    # Remove image
docker rmi -f image                 # Force remove image
docker tag source target            # Tag image

# Image inspection
docker inspect image                # Detailed image info
docker history image                # Image layer history
docker image prune                  # Remove unused images
docker image prune -a               # Remove all unused images
```

## Advanced Docker Commands

### Container Inspection and Debugging
```bash
# Container information
docker inspect container            # Detailed container info
docker logs container               # View container logs
docker logs -f container           # Follow logs in real-time
docker logs --tail 50 container    # Last 50 log lines
docker stats                        # Live resource usage stats
docker stats container              # Stats for specific container
docker top container                # Running processes in container

# Execute commands in containers
docker exec -it container bash     # Interactive shell
docker exec container command      # Execute single command
docker exec -u root container bash # Execute as root user
docker attach container             # Attach to running container
```

### Networking
```bash
# Network management
docker network ls                   # List networks
docker network create mynetwork    # Create custom network
docker network inspect mynetwork   # Network details
docker network connect net container # Connect container to network
docker network disconnect net container # Disconnect from network
docker network rm mynetwork        # Remove network

# Port operations
docker port container               # Show port mappings
docker run -P image                 # Publish all exposed ports
docker run -p 8080:80 image         # Map specific port
docker run -p 127.0.0.1:8080:80 image # Bind to specific interface
```

### Volume Management
```bash
# Volume operations
docker volume ls                    # List volumes
docker volume create myvolume       # Create named volume
docker volume inspect myvolume      # Volume details
docker volume rm myvolume           # Remove volume
docker volume prune                 # Remove unused volumes

# Mount types
docker run -v /host/path:/container/path image    # Bind mount
docker run -v myvolume:/container/path image      # Named volume
docker run --mount type=bind,src=/host,dst=/container image # Mount syntax
docker run --tmpfs /tmp image       # Temporary filesystem
```

## Docker Compose

### Basic Compose Commands
```bash
# Compose operations
docker-compose up                   # Start services
docker-compose up -d                # Start in detached mode
docker-compose down                 # Stop and remove containers
docker-compose down -v              # Also remove volumes
docker-compose start                # Start existing containers
docker-compose stop                 # Stop containers
docker-compose restart              # Restart services
docker-compose pause                # Pause services
docker-compose unpause              # Unpause services

# Service management
docker-compose ps                   # List containers
docker-compose logs                 # View logs
docker-compose logs -f service      # Follow logs for service
docker-compose exec service bash    # Execute command in service
docker-compose run service command  # Run one-off command
docker-compose scale service=3      # Scale service to 3 instances
```

### Compose File Management
```bash
# Build and rebuild
docker-compose build               # Build services
docker-compose build --no-cache    # Build without cache
docker-compose up --build          # Build and start
docker-compose pull               # Pull latest images

# Configuration
docker-compose config              # Validate and view config
docker-compose config --services   # List services
docker-compose -f custom.yml up    # Use custom compose file
```

## Registry and Distribution

### Docker Hub and Registries
```bash
# Authentication
docker login                       # Login to Docker Hub
docker login registry.example.com  # Login to private registry
docker logout                     # Logout

# Image distribution
docker push username/image:tag     # Push to Docker Hub
docker pull username/image:tag     # Pull from Docker Hub
docker search ubuntu              # Search Docker Hub
docker tag local:tag username/repo:tag # Tag for pushing
```

### Private Registry
```bash
# Run local registry
docker run -d -p 5000:5000 --name registry registry:2

# Push to local registry
docker tag myimage localhost:5000/myimage
docker push localhost:5000/myimage
docker pull localhost:5000/myimage
```

## System Management

### System Information and Cleanup
```bash
# System information
docker version                     # Docker version info
docker info                       # System-wide information
docker system df                   # Disk usage
docker system events              # Real-time events
docker system prune               # Remove unused data
docker system prune -a            # Remove all unused data

# Cleanup commands
docker container prune             # Remove stopped containers
docker image prune                # Remove unused images
docker image prune -a             # Remove all unused images
docker volume prune               # Remove unused volumes
docker network prune              # Remove unused networks
```

### Resource Management
```bash
# Resource limits
docker run -m 512m image          # Memory limit
docker run --cpus="1.5" image     # CPU limit
docker run --memory=1g --cpus="2" image # Combined limits
docker update --memory=1g container # Update running container limits

# Resource monitoring
docker stats --no-stream          # One-time stats snapshot
docker stats --format "table {{.Container}}\t{{.CPUPerc}}\t{{.MemUsage}}"
```

## Dockerfile Commands

### Common Dockerfile Instructions
```dockerfile
# Base image
FROM ubuntu:20.04
FROM node:16-alpine

# Metadata
LABEL maintainer="email@example.com"
LABEL version="1.0"

# Environment
ENV NODE_ENV=production
ENV PATH="/app/bin:${PATH}"

# Working directory
WORKDIR /app

# Copy files
COPY . .
COPY package*.json ./
ADD https://example.com/file.tar.gz /tmp/

# Run commands
RUN apt-get update && apt-get install -y curl
RUN npm install --production

# Expose ports
EXPOSE 3000
EXPOSE 8080/tcp

# Volumes
VOLUME ["/data"]

# User
USER node
USER 1000:1000

# Entry point and command
ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["npm", "start"]
```

### Multi-stage Builds
```dockerfile
# Build stage
FROM node:16 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Production stage
FROM node:16-alpine
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
CMD ["node", "dist/index.js"]
```

## Docker Shortcuts and Aliases

### Useful Aliases
```bash
# Add to ~/.bashrc or ~/.zshrc
alias d='docker'
alias dc='docker-compose'
alias dps='docker ps'
alias dpsa='docker ps -a'
alias di='docker images'
alias drmi='docker rmi'
alias drmf='docker rm -f'
alias dex='docker exec -it'
alias dlog='docker logs -f'
alias dstop='docker stop $(docker ps -q)'
alias drm='docker rm $(docker ps -aq)'
alias drmi-all='docker rmi $(docker images -q)'

# Functions
dsh() { docker exec -it $1 /bin/bash; }
dshell() { docker run --rm -it $1 /bin/bash; }
dclean() { docker system prune -af; }
```

### Quick Commands
```bash
# Stop all containers
docker stop $(docker ps -q)

# Remove all containers
docker rm $(docker ps -aq)

# Remove all images
docker rmi $(docker images -q)

# Remove dangling images
docker rmi $(docker images -f "dangling=true" -q)

# Get container IP
docker inspect container | grep IPAddress

# Follow logs of all compose services
docker-compose logs -f

# Rebuild and restart compose service
docker-compose up -d --build service_name
```

## Troubleshooting

### Common Issues and Solutions
```bash
# Container won't start
docker logs container              # Check logs
docker inspect container          # Check configuration
docker events                     # Monitor system events

# Permission issues
docker exec -u root container bash # Run as root
docker run --privileged image     # Run with privileges

# Network issues
docker network ls                 # List networks
docker port container             # Check port mappings
docker exec container netstat -tlnp # Check listening ports

# Storage issues
docker system df                  # Check disk usage
docker volume ls                  # List volumes
df -h                            # Check host disk space

# Performance issues
docker stats                      # Monitor resource usage
docker system events             # Monitor system events
```

### Debug Commands
```bash
# Container debugging
docker run --rm -it --entrypoint=/bin/bash image
docker exec -it container /bin/bash
docker logs --details container
docker inspect --format='{{.State.Health.Status}}' container

# Image debugging
docker history image              # Layer history
docker run --rm -it image sh     # Interactive shell
docker save image | tar -tv      # Examine image contents
```

## Security Best Practices

### Security Commands
```bash
# Scan for vulnerabilities (if using Docker Scout)
docker scout cves image

# Run with security options
docker run --read-only image     # Read-only filesystem
docker run --user 1000:1000 image # Non-root user
docker run --cap-drop ALL image  # Drop all capabilities
docker run --no-new-privileges image # Prevent privilege escalation

# Security inspection
docker inspect --format='{{.Config.User}}' container
docker inspect --format='{{.HostConfig.ReadonlyRootfs}}' container
```

This comprehensive Docker reference covers essential commands for container management, development, and deployment workflows.
