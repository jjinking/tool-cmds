# Docker commands

```bash

# Pull an image or a repository from a registry
docker pull centos

# List docker images
docker images

# Run a docker image
docker run <REPOSITORY>

# Show containers currently running
docker ps

# List of all containers that we ran
docker ps -a

# Run docker and keep it running
docker run -d -t -i centos /bin/bash

# Get a bash shell in the container
docker exec -it <CONTAINER ID> /bin/bash

# Stop a running container
docker stop <CONTAINER ID>

# Remove a stopped container
docker rm <CONTAINER ID>

# Remove all stopped containers
docker rm $(docker ps -a -q)

# Remove docker image from system
docker rmi centos

# Build a docker image with Dockerfile in current directory
docker build -t foo/bar:0.0.1 .
```

## Create private registry
https://docs.docker.com/registry/deploying/

# Start a registry container

```bash
docker run -d -p 5000:5000 --restart=always --name registry registry:2
```

