# docker-cheat-sheet

## Docker build

### Build an image from the Dockerfile in the current directory and tag the image
Traditionally, the Dockerfile is called Dockerfile and located in the root of the context. You use the -f flag with docker build to point to a Dockerfile anywhere in your file system.
```
docker build -f /path/to/a/Dockerfile .
```
You can specify a repository and tag at which to save the new image if the build succeeds:
To tag the image into multiple repositories after the build, add multiple -t parameters when you run the build command:
```
docker build -t shykes/myapp .
docker build -t myimage:1.0 .  
docker build -t shykes/myapp:1.0.2 -t shykes/myapp:latest .

```
### Build using a git repository in a directory called *docker* and the branch *container*:
```
docker build https://github.com/docker/rootfs.git#container:docker
```

### List all images that are locally stored with the Docker Engine 
```
docker image ls 
```
### Delete an image from the local image store 
```
docker image rm alpine:3.4 
```
---

## Share

### Pull an image from a registry  
```
docker pull myimage:1.0  
```

### Retag a local image with a new image name and tag 
```
docker tag myimage:1.0 myrepo/ myimage:2.0  
```
## Push an image to a registry 

```
docker push myrepo/myimage:2.0
```
---

## Run

### Run a container from the Alpine version 3.9 image, name the running container “web” and expose port 5000 externally, mapped to port 80 inside the container. 
```
docker container run --name web -p 5000:80 alpine:3.9
```
### Stop a running container through SIGTERM 
```
docker container stop web 
```
### Stop a running container through SIGKILL 
```
docker container kill web 
```
### List the networks 
```
docker network ls 
```
### List the running containers (add --all to include stopped containers) 
```
docker container ls 
docker container ls -all
```
### Delete all running and stopped containers
```
docker container rm -f $(docker ps -aq) 
```
### Print the last 100  lines of a container’s logs 
```
docker container logs --tail 100 web
```

