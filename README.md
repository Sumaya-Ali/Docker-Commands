# Docker Overview  
============================================  
![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/3a0d9bdf-339a-4a0a-92d8-ce13877fe3ed)  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/7050740b-e374-4eb1-8ebc-46d67929ede2)  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/43a781f4-9150-4aff-be60-c612e390da27)  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/b41f460c-24f2-4189-a822-c52de91ab57b)  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/d19f74da-710a-4e3e-ae84-70a426f84158)  







============================================  
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

to show just images Ids  
docker image ls -q  

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

to remove specific images Ids  
docker image rm $(docker image ls -q)  

============================================  
### 8 to push docker image to DockerHub - after changing the directory to be inside the project folder (ensure to execute docker tag first - find it down below)  

docker push [docker id in DockerHub]/[Reposotry name in DockerHub]:[tag name]  
============================================  
### 9 to stop container from running  

docker stop [container id or container name]  
============================================  
### 10 to restart container (running again after stopping)  

docker start [container name or container id]  
============================================  
### 11 to create a container from an image  

docker run --name [container name] -p [host port: docker image internal port] -d --rm -v [absulot path code folder:docker file 
folder ] -v [some docker folder path to ignore from mapping - anonymous volume] [docker image name or docker image id]:[tag name]  

-- name ==> the name of the container  

-p ==> to define port if it was a web application  

-d ==> undetached to avoid locking the console after running the container but that bot necessarily  

--rm ==> optional to remove the container after stopping it  

-v ==> optional to create volume (connect code folder with docker image folder so the changes reflect immediately after restarting the container - but we still have to build the image if we want to share it -  this solution mint just for development purposes)  

ex: C:\Users\Toshiba\hello-docker\api:/app  

-v(2)[anonymous volume] ==> to ignore some docker folder from original volume. ex: ignore node-modules folder because it can be deleted from the code project and that will cause it to be deleted in the container and the container will no longer work. because of that we create an anonymous volume and map that folder with somewhere else anonymous.  

ex: -v /app/node-modules      

[tag name] ==> image tag (version)- not necessary by default ==> latest  

============================================  
### 12 to remove container  

docker container rm  [container name or container id] [container name or container id] [container name or container id] ...  

we can remove multiple containers  

to remove specific containers Ids  
docker container rm $(docker container ls -aq)  

============================================  
### 13 to remove all images, containers & volumes  

docker system prune -a  
============================================  
### 14 to rename a docker image (to push a docker image in Dockerhub ==> the docker image name must match the repository name (userid + repository name) )  
docker tag [image id or image name] [repository name in dockerhub]:[tag name]  
ex: docker tag hello-docker sumaya95ali/hello-docker:latest  
and only after that we can push image in dockerhub  

============================================  
### 15 to run docker-compose (build images & run containers)  
docker-compose up   
============================================  
### 16 to stop docker-compose (remove the containers but keep images)  
docker-compose down  
to remove all (including volumes)  
docker-compose down --rmi all -v  
============================================  
### 17 to log in to docker  
docker login  
============================================  
### 18 to show docker-compose version  
docker-compose --version  
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







