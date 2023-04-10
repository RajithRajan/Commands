# Cheatsheet for Docker CLI

## Run a new Container 

Start a new Container from an image
```
docker run <IMAGE>
docker run nginx
```

and assign it a name
```
docker run--name <CONTAINER> <IMAGE>
docker run--name web nginx
```

and map a port
```
docker run -p <HOSTPORT>:<CONTAINERPORT> <IMAGE>
docker run -p 8880:80 nginx
```
and map all ports
```
docker run -P <IMAGE>
docker run -P nginx
```

and start container in background
```
docker run -d <IMAGE>
docker run -d nginx
```
and assign it a hostname
```
docker run-hostname <HOSTNAME> <IMAGE>
docker run-hostname srv nginx
```
and add a dns entry
```
docker run-add-host HOSTNAME: IP IMAGE
```

and map a local directory into the container
```
docker run -v <HOSTDIR>: <TARGETDIR> <IMAGE>
docker run -v-/:/usr/share/nginx/html nginx
```
run but to change the entrypoint
```
docker run -it -entrypoint <EXECUTABLE> <IMAGE>
docker run -it-entrypoint bash nginx
```
## Manage Containers

Show a list of running containers
```
docker ps
```

Show a list of all containers
```
docker ps -a
```

Delete a container
```
docker rm <CONTAINER>
docker rm web
```

Delete a running container
```
docker rm -f CONTAINER
docker rm -f web
```

Delete stopped containers
```
docker container prune
```

Stop a running container
```
docker stop <CONTAINER>
docker stop web
```

Start a stopped container
```
docker start <CONTAINER>
docker start web.
```

Copy a file from a container to the host
```
docker ep CONTAINER:SOURCE TARGET
docker op web:/index.html index.html
```

Copy a file from the host to a container
```
docker cp TARGET CONTAINER:SOURCE
docker op index.html web:/index.html
```

Start a shell inside a running container
```
docker exec-it CONTAINER EXECUTABLE
docker exec-it web bash
```

Rename a container
```
docker rename <OLD_NAME> <NEW_NAME>
docker rename 895 web
```

Create an image out of container
```
docker commit CONTAINER
docker commit web
```

## Manage Images\

Download an image
```
docker pull <IMAGE> [TAG]
docker pull nginx
```

Upload an image to a repository
```
docker push <IMAGE>
docker push ayimage:1.0
```

Delete an image
```
docker rmi IMAGE
```

Show a list of all Images
```
docker images
```

Delete dangling images
```
docker image prune
```

Delete all unused images
```
docker image prune -a
```

Build an image from a Dockerfile
```
docker build DIRECTORY
docker build
```

Tag an image
```
docker tag <IMAGE> <NEWIMAGE>
docker tag ubuntu ubuntu: 18.04
```

Build and tag an image from a Docker
```
docker build -t IMAGE DIRECTORY
docker build -t myimage
```

Save an image to tar file
```
docker save <IMAGE>    >   <FILE>
docker save nginx nginx. tar
```
Load an image from a tar file
```
docker load - TARFILE
docker load -i nginx.tar
```

## Info & Stats\

Show the logs of a container
```
docker logs <CONTAINER>
docker logs web
```

Show stats of running containers
```
docker stats
```

Show processes of container
```
docker top <CONTAINER>
docker top web
```

Show installed docker version
```
docker version
```

Get detailed info about an object
```
docker inspect <NAME>
docker inspect nginx
```

Show all modified files in container
```
docker diff CONTAINER
docker diff web
```

Show mapped ports of a container
```
docker port CONTAINER
docker port web
```
