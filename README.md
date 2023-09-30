# Docker-Commands
Repository to explain docker cmd commands
============================================
### 1  to display the docker version in detail or shortly 
docker -version
or
docker -v
============================================
### 2 to display all docker images
docker images
or
docker image ls
============================================
### 3 to display all running containers
docker ps
============================================
### 4 to display all containers
docker ps -a
============================================
### 5 to get docker image from DockerHub
docker pull [docker image name]
============================================
### 6 to build docker image from local project (after adding Dockerfile inside it)
docker build -t [tag name] [docker image name] [docker image path]
-t ==> shortcut for tag (version) by default is (latest) or you can give tag name
change the directory to be inside your project folder so [docker image path] can be just dot .
============================================
### 7 to remove image
docker image rm -f [docker image name or docker image id]
-f ==> shortcut for force - to force removing in case there are related containers to this image but that is normally not necessarily
============================================
### 8 to push docker image to DockerHub - after changing the directory to be inside the project folder
docker push [docker id in DockerHub]/[Reposotry name in DockerHub]:[tag name]
============================================
### 9 to stop conatiner from running
docker stop [container id or container name]
============================================
### 10 to restart conatiner (running again after stopping)
docker start [container name or container id]
============================================
### 11 to create a container from image
docker run --name [container name] -p [host port:docker image internal port] -d [docker image name or docker image id]
-- name ==> the name of container
-p ==> to defines port if it was a web application
-d ==> undetatched to avoid locking the console after running the container but that bot necessarily
============================================




