# Docker

1.  What is Docker
2.  what is container
3.  Why we use Docker
4.  Installation
5.  Apache server
6.  
7.  What are Docker Images
8.  What is a Docker Container
9.  Flow of Docker
10.  Docker Daemon
11.  Docker Client
12. Docker Host
13. Docker Hub/Registry
14. Architecture of Docker
15. Basic Docker Commands
16. Conclusion
17. Reference Links

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

#### To check docker is install or not
```
docker info
```
#### Check the version of Docker :

```
sudo docker --version
```
#### For help in docker
```
docker --help
```
# Container

#### To check the container
```
docker container ls
```
#### How to make a container
when we run command on terminal it will extract data from this website - https://hub.docker.com/
Here, ubuntu is os name 
```
docker container run ubuntu
```
#### See all container
```
docker container ls -a
```
#### Run container in background only for 60 sec
```
docker container run -d ubuntu sleep 60
```
#### Make running container 
```
docker container run -d -it ubuntu
```
#### Stop the container 
```
docker container stop (container id)
```
#### Start the container
```
docker container start (container id)
```
#### Restart the container
```
docker container restart (container id)
```
#### delete a stopped container
```
docker container rm (container id)
```
#### delete a running container
```
docker container rm (container id) -f
```
# Apache server 
Apache is a web server software that is responsible for accepting HTTP requests from visitors and sending them back the requested information in the form of web pages.

#### Make and come inside the container
```
docker container run -it ubuntu /bin/bash
```
#### Exit from the container
```
ctrl+p , ctrl+q
```
#### Come inside the container
```
docker exec -it (id) /bin/bash
```
#### update the container
```
apt-get update
```
#### Install  apache
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
```
service apache2 start
```
#### check the ip add
```
docker container inspect (id)
```
ip add mention in 12th line from last

#### check the output
```
curl (ip)
```
#### check how much space container have used
```
docker container stats (id)
```
# Container port mapping




  # Reference Linkgroups
- https://docs.docker.com
- https://sematext.com/glossary/docker/
- https://www.cherryservers.com/blog/install-docker-ubuntu-22-04
- https://hub.docker.com/
