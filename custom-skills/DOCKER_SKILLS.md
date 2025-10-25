# Docker Skills

## Core Principles for Docker Operations

### 1. Container Management
- ✅ **List containers**: `docker ps -a`
- ✅ **Run container**: `docker run -d --name container_name image_name`
- ✅ **Stop container**: `docker stop container_name`
- ✅ **Remove container**: `docker rm container_name`

### 2. Docker Compose Operations
- ✅ **Start services**: `docker-compose up -d`
- ✅ **Stop services**: `docker-compose down`
- ✅ **Build images**: `docker-compose build --no-cache`
- ✅ **View logs**: `docker-compose logs -f service_name`

### 3. Image Management
- ✅ **List images**: `docker images`
- ✅ **Build image**: `docker build -t image_name .`
- ✅ **Remove image**: `docker rmi image_name`
- ✅ **Pull image**: `docker pull image_name`

### 4. Network Operations
- ✅ **List networks**: `docker network ls`
- ✅ **Create network**: `docker network create network_name`
- ✅ **Connect container**: `docker network connect network_name container_name`

### 5. Volume Management
- ✅ **List volumes**: `docker volume ls`
- ✅ **Create volume**: `docker volume create volume_name`
- ✅ **Mount volume**: `-v volume_name:/path/in/container`

### 6. Health Checks
- ✅ **Container health**: `docker inspect container_name | grep Health`
- ✅ **Service status**: `docker-compose ps`
- ✅ **Logs monitoring**: `docker-compose logs --tail=100 service_name`

### 7. PowerShell Integration
- ✅ **Use semicolons**: `docker ps; docker images`
- ✅ **Proper quoting**: `docker run -d --name "my container" image`
- ✅ **Error handling**: `docker ps 2>$null`

## Common Docker Commands

```powershell
# Container operations
docker ps -a --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"
docker run -d --name "my-app" -p 8080:80 nginx
docker stop "my-app"; docker rm "my-app"

# Docker Compose operations
docker-compose -f "path\to\docker-compose.yml" up -d
docker-compose -f "path\to\docker-compose.yml" down
docker-compose -f "path\to\docker-compose.yml" build --no-cache

# Health monitoring
docker inspect "my-app" | ConvertFrom-Json | Select-Object -ExpandProperty State
docker-compose logs --tail=50 -f service_name
```

## Error Handling
- ✅ **Check container status**: `docker ps -a | findstr container_name`
- ✅ **View container logs**: `docker logs container_name`
- ✅ **Inspect container**: `docker inspect container_name`
- ✅ **Clean up**: `docker system prune -f`

These rules are critically important for proper Docker operations in Windows PowerShell environment.
