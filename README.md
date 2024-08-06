# Docker

1.  What is Docker
2.  what is container
3.  Why we use Docker
4.  Installation
5.  What is a Dockerfile
6.  What are Docker Images
7.  What is a Docker Container
8.  Flow of Docker
9.  Docker Daemon
10.  Docker Client
11. Docker Host
12. Docker Hub/Registry
13. Architecture of Docker
14. Basic Docker Commands
15. Conclusion
16. Reference Links

![docker](https://github.com/user-attachments/assets/d1ed98b0-fd20-4af5-9a88-2db45d5c6911)
    
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
 ```
 lsb_release -a
```
### RAM 
At least 2 GB of RAM
#### How to check the RAM?
 ```
 free -h
```
#### Step 1. up-to-date system by using following command :
```
 sudo apt-get update
```
sometime curl package is not install in system, To install curl use this command: 
```
 sudo apt-get install curl
```
#### Step 2. Install the dependency packages required to install Docker.
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
#### Step 3.Install Docker
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


  # Reference Link
- https://docs.docker.com
- https://sematext.com/glossary/docker/
- https://www.cherryservers.com/blog/install-docker-ubuntu-22-04
