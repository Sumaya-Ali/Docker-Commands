# Docker Overview  
============================================  
![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/3a0d9bdf-339a-4a0a-92d8-ce13877fe3ed)  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/7050740b-e374-4eb1-8ebc-46d67929ede2)  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/43a781f4-9150-4aff-be60-c612e390da27)  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/b41f460c-24f2-4189-a822-c52de91ab57b)  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/d19f74da-710a-4e3e-ae84-70a426f84158)  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/2f4e476f-625b-4fa2-bfad-4be9bb3081ce)  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/e4e68562-1857-4eaf-83bd-6147ce01fe76)  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/a6af4cdf-7757-4e91-ad79-f37449a27c7e)  

============================================  
to add docker to Visual Studio:  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/1309ad85-aa3c-481b-9f37-7afd8ec55573)  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/939ae456-74fa-4156-88a2-7d8186bae506)  

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

docker run --name [container name] -e [environment variable]=[value] -p [host port: docker image internal port] -d --rm -v [absulot path code folder:docker file 
folder ] -v [some docker folder path to ignore from mapping - anonymous volume] [docker image name or docker image id]:[tag name]  

-- name ==> the name of the container  

-e ==> environment variable  ex: -e db_name = sumaya   (could be multiple environment variables)  

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
### 17 to log in to docker  
docker login  
============================================  
### 18 to show docker networks  
docker network ls  
============================================  
### 19 to debug container  
docker exec -it -u root [container id] sh  
-it ==> interactive mode  
[container id] ==> we can write just the first three letters of container id  
-u ==> user id ex: root (optional)  
============================================  

============================================  
### Docker Compose Commands:
============================================  
### 1 to show docker-compose version  
docker-compose --version  
============================================  
### 2 to run docker-compose (build images & run containers)  
docker-compose up --build -d   
-- build ==> to only build images  
-d ==> detached mode (for not blocking terminal)  
============================================  
### 3 to stop docker-compose (remove the containers but keep images)  
docker-compose down  
to remove all (including volumes)  
docker-compose down --rmi all -v  
============================================  
### 4 to build docker-compose  
docker-compose build --no-cache  
--no-cache ==> for not using cached images  
============================================  
### 5 to show running container in docker-compose  
docker-compose ps  
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

============================================  
Docker Compose:  
============================================  
we use a docker-compose file when we have multiple containers (or just one) because it is easier to build containers that the run commands, and it takes the similar attribuits  

============================================  
Multi Staging in Docker file:  
============================================  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/664d0939-25a8-4ec5-9607-8f81d727b544)  

in the case of dotNetCore projects, we use multi staging docker file because we need dotNetSDK image to build the docker image but that version is too big, thats whay we use a runtimeASP version to deploy the image after building it.  

============================================  
Docker Networks:  
============================================  
when we have a DB in our project, we must build a specific container for it in docker-compose  
we want our container to communicate with DB container, that is why we define them in the same network  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/e47a9a0a-83b6-4964-ae7d-83d95fd680a2)  

============================================  
passing Environment Variables:  
============================================  
when we have DB, Logs, .. etc. we pass environment variables to the container (through docker-compose) which is used in code to define (the path of the log file, DB server, DB host, DB User ID/Password, ..etc.  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/aeabf866-7ec7-421c-b0ff-e8a04ccfcea5)  

![image](https://github.com/Sumaya-Ali/Docker-Commands/assets/52631071/1c88729b-d16e-4e98-ba9e-ddc89832c082)  












