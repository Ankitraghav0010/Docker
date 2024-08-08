# Docker
![docker](https://github.com/user-attachments/assets/d1ed98b0-fd20-4af5-9a88-2db45d5c6911)

# Table of content

1.  What is Docker
2.  What is container
3.  Why we use Docker
4.  Installation
5.  Container
6.  Apache server 
7.  Container port mapping
8.  Import the data from system 
9.  Docker image
10. Docker hub 
11. Docker volume
12. Docker swarm
13. Conclusion
14. Reference Links


    
  # What is Docker?
  Docker is a tool that keeps everything your app needs in one place.Docker provide platform as a service (PaaS) that use OS-level virtualization to deliver software in packages called containers.

  # What is Container?
  Container is like a box that provide a way of creating an isolated environment,in which applications and their dependencies can live.

  # Why we use Docker?
  We use Docker for several key reasons:
  ### Cost-saving: 
  Docker containers use far less memory, especially when compared to their counterparts (virtual machines). Thus, you spend less on IT infrastructure resources.
  
  ### Isolation:
  Docker containers are isolated from each other and from the host system, which helps prevent conflicts between applications and improves security.
  
### Rapid Prototyping:
Docker allows developers to quickly create and test new features or applications without setting up complex environments.

### Easy Setup: 
Docker makes setting up applications straightforward. You don’t need to manually install and configure software; everything the app needs is in the container.

# Installation
### version
 Ubuntu 20.04.6 LTS
 #### How to check the version?
 
 Paste this command in terminal  to check the version.
 ```
 lsb_release -a
```
### RAM 
At least we have 2 GB of RAM in our system to run docker.
#### How to check the RAM?

Paste this command in terminal  to check the RAM.
 ```
 free -h
```
#### Step 1. up-to-date system by using following command :

Paste this command in terminal to update your system.
```
 sudo apt-get update
```
- sometime curl package is not install in system, To install curl use this command: 
```
 sudo apt-get install curl
```
#### Step 2. Install the dependency packages required to install Docker.

Paste this command in terminal  to Install the dependency packages.
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
#### Step 3.Install Docker

Paste this command in terminal  to install docker
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
Next, add the Docker APT repository to your system in the sources.list.d directory.
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
update the local package index once more.
```
sudo apt update
```
Now, install Docker Community Edition 
```
sudo apt install docker-ce -y
```
Once installed, the Docker daemon or service should be running. To confirm this, run the command:
```
sudo systemctl status docker
```
#### To check docker is install or not

Paste this command in terminal  to check docker is install or not.
```
docker info
```
#### Check the version of Docker :

Paste this command in terminal  to check the version of Docker.
```
sudo docker --version
```
#### For help in docker

Paste this command in terminal for docker related command help.
```
docker --help
```
# Container

#### To check the container

Paste this command in terminal to check the containers list.
```
docker container ls
```
#### How to make a container
when we run command on terminal it will extract data from this website - https://hub.docker.com/
Here, ubuntu is OS name 
```
docker container run ubuntu
```
#### See all container
Paste this command in terminal to check running and stopped container list.
```
docker container ls -a
```
#### Run container in background only for 60 sec

Paste this command in terminal and container will run in background only for 60 sec.
```
docker container run -d ubuntu sleep 60
```
- -d Stands for :Detached mode
- Purpose: Runs the container in the background.
#### Make running container 

Paste this command in terminal create a running container.
```
docker container run -d -it ubuntu
```
- -it Stands for: Interactive 
- Purpose: Allows you to interact with the container.

#### Stop the container 

Paste this command in terminal with your conatiner id and it will stop.
```
docker container stop (container id)
```
#### Start the container

Paste this command in terminal with your conatiner id and it will start.
```
docker container start (container id)
```
#### Restart the container

Paste this command in terminal with your conatiner id and running container will restart.
```
docker container restart (container id)
```
#### delete a stopped container

Paste this command in terminal with your conatiner id and it will deleted.
```
docker container rm (container id)
```
#### Delete a running container

Paste this command in terminal with your conatiner id and your running container will be deleted.
```
docker container rm (container id) -f
```
# Apache server 
Apache is a web server software that is responsible for accepting HTTP requests from visitors and sending them back the requested information in the form of web pages.

#### Create and come inside the container

Paste this command in terminal you will come inside the new container.
```
docker container run -it ubuntu /bin/bash
```
#### Exit from the container

Paste this command in terminal and you will exit from container.
```
ctrl+p , ctrl+q
```
#### Come inside the container

Paste this command in terminal you will come inside the container.
```
docker container attach (id)
```
or
```
docker exec -it (id) /bin/bash
```
#### Update the container

Paste this command in terminal inside the container ,container will be updated.
```
apt-get update
```
#### Install  apache

Paste this command in terminal and apache will install into your container.
```
apt-get install apache2
```
Now come inside the folder
```
cd /var/www/html/
```
add welcome to keen&able
```
echo "welcome to keen&able" >index.html
```
#### Restart the service

Paste this command in terminal to restart apache service.
```
service apache2 start
```
#### Check the ip add

Paste this command in terminal to check ip of container. 
```
docker container inspect (id)
```
- ip add mention in 12th line from last

#### Check the output


Paste this command in terminal to check apache server output on terminal.
```
curl (ip)
```
#### Check how much space container have used

Paste this command in terminal with container id to check space used by container.
```
docker container stats (id)
```
# Container port mapping
In Docker, port mapping is the process of making a specific port of a container accessible from the host machine or network. This allows services running inside the container to be accessed externally.
#### Create container with port no 

Paste this command in terminal to create container with changed port no
```
docker container run -it -p 3600:80 ubuntu /bin/bash
```
#### Install apache

Paste this command in terminal to install apache 
```
apt-get install apache2
```
Now come inside the folder
```
cd /var/www/html/
```
add welcome to keen&able
```
echo "welcome to keen&able" >index.html
```
#### Restart the service

Paste this command in terminal to start service.
```
service apache2 start
```
#### Now check your system ip in another tab
Paste this command in another terminal to check ip
```
ifconfig
```
#### Paste this on web browser
paste the ip with port no then data will be visible on webserver.
```
ip add :3600
```
## Change container name

Paste this command in terminal change the container name.
```
docker container rename (id) (new name)
```
## Pause the container

Paste this command in terminal to pause the container.
```
docker container pause (id/name)
```
## Unpause the container
Paste this command in terminal to unpause the container.
```
docker container unpause (id/name)
```
# Import the data from system 

Paste this command in terminal to copy data from system and paste into conatiner.
```
docker container cp docker.svg (id):/[location(tmp)]
```
# Docker image
Docker images are used to create containers, which are instances of these images running in an isolated environment.

#### Export and import the container

Paste this command in terminal to export the container data into a file.
```
docker container export ID>(file name)
```
#### Create image

Paste this command in terminal to import and making image by the container's file
```
docker image import (filename) imagename
```
#### Create container with image

Paste this command in terminal to create container with image.
```
docker container run -it imagename /bin/bash
```
#### Create image directly
In last two commands firstly we have to export the data in file then convert to docker image
Now, we can create image directly 
```
docker container commit (id) imagename
```
#### To check

Paste this command in terminal to  check image list.
```
docker image ls
```
# Docker hub
Docker Hub is a container registry built for developers and open source contributors to find, use, and share their container images.
![Docker-hub-registry(1)](https://github.com/user-attachments/assets/57b90ca6-9356-4fe0-a3b2-d4bbaf000bf8)


- visit https://hub.docker.com/
- create an account

## Pull image
There is following steps to pull the image:
- search image name in search bar
- copy the command
- paste the command in your terminal

  for instance, I want a mysql image  then I searched the my sql and copy
  ```
  docker pull mysql
  ``` 
## Push image
There is following steps to push the image: 
- create docker tag
- login into docker acc via cli mode
- push the image
  
Note : you have make unique name for image, same name image is not acceptable.<br>
you have to create tag in same manner that is given below.
### docker tag

Paste this command in terminal to tag the image
```
docker tag imagename username/(any name)
```
### Login via cli into docker hub account

Paste this command in terminal to login via cli into docker hub account
```
docker login
```
### Push the image

Paste this command in terminal to push image on docker hub.
```
docker push (imagename)/{ar2002/webimage}
```
Now, In whole world your image will available on docker hub.

# Docker volume
A Docker volume is a storage, that is attached to conatiner and store all the data of container if in case container is stopped or crash than we can use this volume.
### Check volume

Paste this command in terminal to check volume.
```
docker volume ls
```
### For help

Paste this command in terminal for image related help.
```
docker volume --help
```
 ### Create volume

 Paste this command in terminal to create volume.
 ```
docker volume create (volume name)
```
### Check path

Paste this command in terminal to check the path of volume.
```
docker volume inspect myvol
```
### Copy path and paste in terminal 

Paste this command in terminal to come inside the volume.
```
cd /var/lib/docker/volumes/myvol/_data
```
### Create some file

Paste this command in terminal to create some file inside the terminal.
```
touch abc{1..10}
```

### Create container with attach volume

Paste this command in terminal to create  container with attached volume.
```
docker container run -it -v (vol name):/tmp --name (xyz) ubuntu /bin/bash
```
### Check volume data is available or not

Paste this command in terminal to check volume's data that we have attached. 
```
cd /mnt/
```

# Docker swarm
Docker Swarm is a tool that allows you to manage workers by an individual manager.
Manager can manage container,image and volume at workers node.


Docker Swarm is made up of two main components:

- Manager Nodes / Master Nodes
- Worker Nodes

![jdbsqluohzrw5ku5l096](https://github.com/user-attachments/assets/41d87518-8eea-4d17-8eb1-f2673a8e5e8a)

Docker swarm needs multiple OS to deploy the service, we can deploy it on any cloud like AWS but it is not open source that's  why basic info is mentaion here about docker swarm.

# Conclusion
Docker is a platform that make easy the process of building, shipping, and running applications in containers. Containers are lightweight, portable, and consistent across different environments.

  # Reference Linkgroups
- https://docs.docker.com
- https://sematext.com/glossary/docker/
- https://www.cherryservers.com/blog/install-docker-ubuntu-22-04
- https://hub.docker.com/
- https://dev.to/shankarsurya035/how-to-install-and-configure-docker-swarm-on-linux-oe0
