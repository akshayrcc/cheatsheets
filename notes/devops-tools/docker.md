# docker

![Image of Docker Architecture](img/docker-architecture.png)


## Table of Contents

   * [Basic commands](#Basic-commands)
   * [Containers](#Containers)
   * [Images](#Images)
   * [Exposing Ports](#Exposing-Ports)
   * [Container Networking](#Container-Networking)
   * [Legacy Linking](#Legacy-Linking)
   * [Volumes](#Volumes)
   * [Registries](#Registries)
   * [Dockerfiles](#Dockerfiles)
   * [Docker Compose](#Docker-Compose)
   * [Orchestration Options](#Orchestration-Options)
   * [Running a My-SQL Container](#Running-a-My-SQL-Container)
   * [Running an angular app from a dockerfile](#Running-an-angular-app-from-a-dockerfile)
   

## Basic commands:

```sh
docker --version
docker info
docker hello-world
```

* To run linux container and run bash in it:
`docker run -it ubuntu:latest  bash`
 (it stands for  interactive terminal)
 
## Containers

	When we run an image we get a container.
* To see running container:
	`docker ps`

* To see running container with format:
```sh
	FORMAT=\nID\t{{.Id}}\nIMAGE\t{{Image}}
	echo $FORMAT
	docker ps --format $FORMAT
```
* Check the last container:
	`docker ps -l` 

* Make docker images out of container, return image_id:
	`docker commit container_id`

* To give image a name:
	`docker tag image_id my-image`

* Short-hand to commit and give image a name:
	`docker commit container_name my-image2`

* Test my-image by running process 'bash' in it
	`docker run -it my-image bash`

* Run container for 5 sec
	`docker run --rm -it ubuntu sleep 5`

* Run container with bash commands
```
	docker run -it ubuntu bash -c "sleep 3; echo all done"
	docker run --name my_container
```

* Run and detach the container
	`docker run -d -it ubuntu bash`

* attach the container 
	`docker attach container_name`

* detach container
	`ctrl P ctrl Q `

* use same container parallely and start bash
	`docker exec -ti container_name bash`

* To exit container
	`ctrl D`

* Logs
	`docker logs container_name`

* Killing and removing docker container
	`docker kill container_name`
	`docker rm container_name`

* We can add memory constraints, CPU limits and various orchestrations to docker container

* Building the container
	`docker build -t container_build01`

## Images

* Check present docker images:
	```
	docker images
	docker rmi image_name
	```
	
* Running the image:
	`docker run -d -p 80:80 \ --name docker_img01 container_build01`

* Pulling an image
	`docker pull img_name:version_no`

* Pushing image to docker hub
	```
	docker login
	docker tag docker_img01 akshaychaudhari/my-image01
	docker push akshaychaudhari/my-image01
	```
* Docker registry
	`docker run -d -p 5000:5000 --restart-always --name registry registry:2`

* Saving an image
	`docker save -o my-images.tar.gz existing_image_name`

* Loading image
	`docker image -i my-images.tar.gz`
	
## Exposing Ports

* Setting and mapping ports of container and local machine:  
	`docker run --rm --it -p 45678:45678 -p 45679:45679 --name echo-server  ubuntu:14.04 bash`
	
* Container's are not reliable to directly address other container's by IP Address. We can use 'host.docker.internal' instead localhost/ tnsname/ip address of the container.

* If only intenal ports are given, docker assign external ports automatically. Those can be checked using:  
	`docker port container_name`

* This works with UDP Protocal as well as like TCP above.  
	`docker run outside_port:inside_port/protocol`

* UDP example using netcat:
	- at server:  
	`nc -ulp 45678`
	- at client:  
	`docker port echo-server;  nc -u localhost 327771;`

## Container Networking

```
	docker network ls
	docker create networt net_01
```
* runing a container on specific network
	`docker run --rm -it --net net_01 --name dogserver ubuntu:14.01 bash `

* containers in the same newtork can only commmunciate.
* adding an exising container to a network.
	`docker network connect net_02 catserver`

## Legacy Linking

* One way linking of the port between 2 m/c.
	```
	docker run --rm -it -e SECRECT=jingalala --name catserver  ...
	docker run --rm -it --link catserver --name dogserver
	```
## Volumes

* These are virtual disks for local disk host.
1. Persistent
* will persist on host if all containers are killed
	`docker run -it -v 'C:\user\akshay':/shared-folder ubuntu bash`

2. Ephermal
* will evaporate once no container is using it.
	```
	docker run -it -v /shared-folder ubuntu bash
	docker run -it --volume-from container_name_having_volume ubuntu bash
	```
## Registries

* It manages and distributes images
	`docker search ubuntu`

## Dockerfiles

* Building images with code.
	`docker build -t name-of-result_img docker-file-location`
* Not a shell scrpit, its just like it.
* Process started on one line wont be running next line.
* Each step is cached.
* Each line is its own call to docker run
* Env variable persist one multiline if we use ENV command.

* Sample dockerfile 01:
```sh
FROM debian:sid
RUN apt-get -y update
RUN apt-get install nano
CMD ["/bin/nano" "/tmp/notes"]
```
	`docker build -t example/new-img-02 .`

* Sample dockerfile 02:
```sh
MAINTAINER akshay chaudhari <akshaychaudhari12345@gmail.com>
FROM example/my-img-02
ADD notes.txt /notes.txt
ENV DB_HOST=db.prod.example.com
ENV DB_PORT=5432
CMD "nano" "/notes.txt"
```
	`docker build -t example/new-img-02 .`

* Avoid golden images creation. Always include all the dependecies.

* Get the process id for given docker container
	`docker inspect --format '{{.State.Pid}}' container_name`

## Docker Compose:  

	```
	docker compose up
	docker compose stop
	```
Docker compose is basically used to work with multiple docker containers. For eg. a MEAN stack application could have 3 containers viz. client, server and database.
So, to set it up in one go we can use docker compose command.
This calls the docker-compose.YML file in the root directory and runs the respective containers as per docker-compose.YML file.
Sample yml file:
```
version: "3.8"
services:
  webapp:
    build: ./dir
```

Read More at: https://docs.docker.com/compose/compose-file/


## Orchestration Options:
1. Kubernates
2. Amazon EC2 Container Service (ECS)
3. AWS fargate
4. Docker sworm
5. Google Kubernates Engine
6. MS Azure Kubernates Service


## Running a My-SQL Container:
```sh
docker run --name akshay-mysql2 -e MYSQL_ROOT_PASSWORD=root123 -d mysql -p 3306:3306

docker run --name akshay-mysql3 -e MYSQL_ROOT_PASSWORD=root123 -d mysql -h localhost -P 3306 --protocol=tcp

docker run -it --network first-network --rm mysql mysql -h akshay-mysql -u first-user -p

docker run -it --rm mysql mysql -hsome.mysql.host -usome-mysql-user -p

mysql -h localhost -P 3306 --protocol=tcp -u root
```

## Running an angular app from a dockerfile:
1. First write your dockerfile into root directory of your app (eg. /my-app/)
Eg. dockerfile
```
	FROM node:6
	RUN mkdir -p /usr/src/app
	WORKDIR /usr/src/app
	COPY package.json /usr/src/app
	RUN npm cache clean
	RUN npm install
	COPY . /usr/src/app
	EXPOSE 4200
	CMD ["npm","start"]
```

2. Invoke dockerfile using build to create an image for your project.  
 `docker build -t top-movie-app /app-root-path/`

3. Then run docker image on given port.  
	`docker run --rm -p 4200:4200  --name "TopMovies001" top-movie-app `
	
