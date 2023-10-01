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
docker build -t [docker image name]: [tag name] [docker image path]
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
### 9 to stop container from running
docker stop [container id or container name]
============================================
### 10 to restart container (running again after stopping)
docker start [container name or container id]
============================================
### 11 to create a container from an image
docker run --name [container name] -p [host port: docker image internal port] -d [docker image name or docker image id]:[tag name]
-- name ==> the name of the container
-p ==> to define port if it was a web application
-d ==> undetached to avoid locking the console after running the container but that bot necessarily
[tag name] ==> image tag (version)- not necessary by default ==> latest
============================================
### 12 to remove container
docker container rm  [container name or container id] [container name or container id] [container name or container id] ...
we can remove multiple containers
============================================
### 13 to remove all images, containers & volumes
docker system prune -a
============================================
============================================
Explains Dockerfile commands:
============================================

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/df217047-be0b-4a91-9994-f8945f61a012)

### FROM => parents docker image (operating system & environment [Node/Ruby/Python/......] / could be installed locally or downloaded from DockerHub
###  COPY ==> to copy all project files to some directory in order to package them & dockerized them
### WORKDIR ==> to change the working directory to the newly created folder in order to run the following commands on project files
### CMD ==> to execute the command that is responsible for creating instances and starting containers (could be running multiple times)

============================================

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/321582a4-0244-4900-a313-1d989075fe4e)

### RUN ==> to execute commands just one time (while building the docker image ) In this case we want to collect the project dependencies (node modules/packages..)
### EXPOSE ==> to declare the internal docker image port (in case of a web application) [according to the defined port in the project code] .. this instruction is not necessary but highly recommended

============================================
![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/9d7c9dc8-a375-4b23-a4b2-29a92788ef85)

### .dockerignore file to ignore some files or extensions from dockeriz ex: node-modules / logs / .. etc

============================================
### Layer caching 
to avoid rebuilding unnecessary docker image layers when we change something in the project code because docker will rebuild COPY instruction and all the layers below it. we change the order of layers and put [RUN npm install] above COPY in order to cache it so there is no need to rebuild this layer
the modified layer and all layers below it will be rebuilt -  Docker gets the above layers from cach. 
![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/7af9734c-43bb-4502-86e6-23776d9231a3)







