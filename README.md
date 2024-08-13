# Docker
![docker](https://github.com/user-attachments/assets/d1ed98b0-fd20-4af5-9a88-2db45d5c6911)

## Table of content

1.  Introduction to Docker
2.  Introduction to Container
3.  Use of Docker
4.  Installation
5.  Container
6.  Apache server 
7.  Container port mapping
8.  Import the data from the system 
9.  Docker image
10. Docker hub 
11. Docker volume
12. Docker swarm
13. Conclusion
14. Reference links


    
  # Introduction to Docker
  Docker is a tool that keeps everything your app needs in one place. Docker provides a platform as a service (PaaS) that uses OS-level virtualization to deliver software in      container packages.

  # Introduction to Container
  A container is like a box that creates an isolated environment where applications and their dependencies can live.

  # Reason to Use of Docker
  We use Docker for the following key reasons:
  ### Cost-saving: 
  Docker containers use less memory, Thus, you spend less amount on IT infrastructure.
  
  ### Isolation:
  Docker containers and the host system are isolated from each other, which helps prevent conflicts between applications and improves security.
  
### Rapid Prototyping:
Docker allows developers to quickly create and test new features or applications without setting up complex environments.

### Easy Setup: 
Docker makes setting up applications straightforward. You don’t need to install and configure software manually; everything the app needs is in the container.

# Installation
### version
 Ubuntu 20.04.6 LTS
 #### How to check the version?
 
 Paste this command in the terminal  to check the version.
 ```
 lsb_release -a
```
- lsb_release: Stands for "Linux Standard Base release." It is a command-line tool that provides information about the Linux distribution's release.
- -a: This option stands for "all." It instructs the command to display all available information.
### RAM 
At least we have 2 GB of RAM in our system to run docker.
#### How to check the RAM?

Paste this command in the terminal  to check the RAM.
 ```
 free -h
```
- free: This command displays the total amount of free and used physical memory (RAM) and swap memory in the system, as well as the buffers and caches used by the kernel.

- -h: This option stands for "human-readable." It modifies the output to be in a format that is easier to read, typically using units like KB, MB, or GB instead of displaying the memory in bytes.
#### Step 1. Up-to-date system by using the following command :

Paste this command in the terminal to update your system.
```
 sudo apt-get update
```
- sudo: This prefix stands for "superuser do." It allows you to run commands with elevated privileges (as an administrator) that may be required for certain operations, like updating the system.

- apt-get: APT: Stands for Advanced Package Tool, a command-line tool for handling packages. It allows you to install, update, and remove software packages.

- update: This subcommand tells apt-get to download the latest package lists from the repositories specified in your system's configuration files (typically found in /etc/apt/sources.list)
#### Step2: Sometimes the curl package is not installed in the system, To install curl use this command: 
```
 sudo apt-get install curl
```
curl: This is the name of the package you want to install. curl is a command-line tool used to transfer data from a server. It supports various protocols, including HTTP, HTTPS, and FTP.
#### Step 3. Install the dependency packages to install Docker.

Paste this command into the terminal to install the dependency packages.
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
- sudo: Runs the command with superuser or administrator privileges.

- apt install: Installs the specified packages.

- apt-transport-https: Enables apt to retrieve packages over the HTTPS protocol, which is more secure than HTTP.

- ca-certificates: Installs digital certificates to ensure the system can verify the authenticity of HTTPS connections.

- curl: A command-line tool for transferring data using various protocols, such as HTTP, HTTPS, and FTP.

- software-properties-common: Provides tools to manage software repositories, including adding new ones
#### Step 4. Install Docker

Paste this command in the terminal  to install docker.
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
- curl -fsSL: This part of the command downloads the Docker GPG key from the specified URL.<br>
-f(fail): Stops the command if the server returns an error.<br>
-s(silent): Runs the command quietly without showing the progress bar.<br>
-S(show errors): Ensures errors are still shown even if -s is used.<br>
-L(follow redirects): Follows any redirects to download the file.<br>
- |: This is a pipe operator that passes the output of the curl command directly to the next command.

- sudo gpg --dearmor: This command converts the downloaded GPG key from ASCII (armored format) to binary format.
- gpg: Stands for GNU Privacy Guard, a tool for secure communication and data storage.
- --dearmor: Converts the key from its armored (text) format to a binary format.

- -o /usr/share/keyrings/docker-archive-keyring.gpg: This specifies the output file where the binary GPG key will be stored.
- /usr/share/keyrings/: A directory commonly used to store keyrings for authentication.
- docker-archive-keyring.gpg**: The name of the file where the Docker GPG key is saved in binary format
  
Add the Docker APT repository to your system in the sources.list.d directory.
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
- deb: Specifies a Debian package repository.
- [arch=$(dpkg --print-architecture)]: Includes the system architecture (e.g., amd64).
- signed-by=/usr/share/keyrings/docker-archive-keyring.gpg: Uses Docker's GPG key for package verification.
- https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable: URL leads to the specific location where Docker's stable version for your particular Ubuntu version can be downloaded and installed.
- sudo tee /etc/apt/sources.list.d/docker.List: This information is saved in a new file for the package manager to use.
-  /dev/null: no output or feedback from the command is displayed to the user.<br>

update the local package index once more.
```
sudo apt update
```
Now, install Docker Community Edition:
```
sudo apt install docker-ce -y
```
docker-ce: Specifies the package name for Docker Community Edition, which is the free, open-source version of Docker.<br>

-y: Automatically answers "yes" to any prompts that may appear during the installation process.<br>
Once you have installed the Docker daemon or service, it should be running. To confirm this, run the command:
```
sudo systemctl status docker
```
![Screenshot from 2024-08-13 15-45-30(1)](https://github.com/user-attachments/assets/adf0f39e-dbff-432e-b090-ff8abfcf263f)

#### To check whether docker is installed or not

Paste this command in the terminal  to check whether docker is installed or not.
```
docker info
```
#### Check the version of Docker :

Paste this command in the terminal to check the Docker version.
```
sudo docker --version
```
![Screenshot from 2024-08-13 15-46-07](https://github.com/user-attachments/assets/927996af-8cc4-4454-afcf-4be471217c8a)
#### For help in docker

Paste this command in the terminal for docker-related command help.
```
docker --help
```
# Container

#### To check the container

Paste this command in the terminal to check the containers list.
```
docker container ls
```
#### How to make a container
When we run the command on the terminal it will extract data from this website - https://hub.docker.com/
Here, ubuntu is the OS name.
```
docker container run ubuntu
```
#### See all container
Paste this command in the terminal to check the running and stopped container list.
```
docker container ls -a
```
#### Run container in the background only for 60 sec

Paste this command in the terminal and the container will run in the background only for 60 sec.
```
docker container run -d ubuntu sleep 60
```
- -d Stands for Detached mode.
- Purpose: Runs the container in the background.
#### Make a running container 

Paste this command in the terminal to create a running container.
```
docker container run -d -it ubuntu
```
- -it Stands for Interactive 
- Purpose: Allows you to interact with the container.

#### Stop the container 

Paste this command in the terminal with your container ID and it will stop.
```
docker container stop container id
```
#### Start the container

Paste this command in the terminal with your container ID and it will start.
```
docker container start container id
```
#### Restart the container

Paste this command in the terminal with your container ID and the running container will restart.
```
docker container restart container id
```
#### Delete a stopped container

Paste this command in the terminal with your container ID and it will deleted or removed.
```
docker container rm container id
```
#### Delete a running container

Paste this command in the terminal with your container ID and your running container will be deleted forcefully (-f).
```
docker container rm container id -f
```
# Apache server 
Apache is a web server tool that accepts visitors' HTTP requests and sends them back the requested information in the form of web pages.

#### Create and come inside the container

Paste this command in the terminal, and you will come inside the new container.
```
docker container run -it ubuntu /bin/bash
```
#### Exit from the container

Press this command in the terminal and you will exit from the container.
```
ctrl+p 
```
```
ctrl+q
```
#### Come inside the container

Paste this command in the terminal, and you will come inside the container.
```
docker container attach id
```
#### Update the container

Paste this command in the terminal inside the container, and the container will be updated.
```
apt-get update
```
#### Install  apache

Paste this command in the terminal and Apache will install it into your container.
```
apt-get install apache2
```
Now come inside the folder:
```
cd /var/www/html/
```
Add welcome to keen&able.
```
echo "Welcome to keen&able" >index.html
```
#### Start the service

Paste this command in the terminal to restart the Apache service.
```
service apache2 start
```
#### Check the IP add

Paste this command in the terminal to check the container's IP. 
```
docker container inspect id
```
- ip add a mention in the 12th line from the last

#### Check the output

Paste this command in the terminal to check the Apache server output on the terminal.
```
curl IP
```
#### Check how much space the container has used

Paste this command in the terminal with the container ID to check the space used by the container.
```
docker container stats id
```
# Container port mapping
In Docker, port mapping is the process of making a specific port of a container accessible from the host machine or network. This allows services running inside the container to be accessed externally.
#### Create a container with port no 

Paste this command in the terminal to create the container with changed port no.
```
docker container run -it -p 3600:80 ubuntu /bin/bash
```
#### Install apache

Paste this command in the terminal to install Apache.
```
apt-get install apache2
```
Now come inside the folder:
```
cd /var/www/html/
```
Add welcome to keen&able.
```
echo "Welcome to keen&able" >index.html
```
#### Start the service

Paste this command in the terminal to start the service.
```
service apache2 start
```
#### Now check your system ip in another tab
Paste this command in another terminal to check the IP
```
ifconfig
```
#### Paste this on the web browser
Paste the IP with port no, and then data will be visible on the webserver.
```
ip add:3600
```
## Change container name

Paste this command in the terminal to change the container name.
```
docker container rename id new name
```
## Pause the container

Paste this command in the terminal to pause the container.
```
docker container pause id/name
```
## Unpause the container
Paste this command in the terminal to unpause the container.
```
docker container unpause id/name
```
# Import the data from the system 

Paste this command in the terminal to copy data from the system and paste it into the container's location.
```
docker container cp docker.svg id:/location
```
# Docker image
Docker images are used to create containers, which are instances of these images running in an isolated environment.

#### Export and import the container

Paste this command in the terminal to export the container data into a file.
```
docker container export ID>file name
```
#### Create image

Paste this command in the terminal to import and make an image using the container's file.
```
docker image import filename image name
```
#### Create a container with an image

Paste this command in the terminal to create a container with an image.
```
docker container run -it image name /bin/bash
```
#### Create an image directly
In the last two commands firstly we have to export the data in a file and then convert it to a docker image.
Now, we can create images directly 
```
docker container commit id image name
```
#### To check

Paste this command in the terminal to  check the image list.
```
docker image ls
```
# Docker hub
Docker Hub is a container registry built for developers and open-source contributors to find, use, and share their container images.
![Docker-hub-registry(1)](https://github.com/user-attachments/assets/57b90ca6-9356-4fe0-a3b2-d4bbaf000bf8)


- visit https://hub.docker.com/ 
- create an account.
![Screenshot from 2024-08-13 15-48-33](https://github.com/user-attachments/assets/8ddcfe60-e8ed-4259-a24f-35ad4e805903)

## Pull image
There are the following steps to pull the image:
- Search the image name in the search bar.
- Copy the command.
- Paste the command in your terminal.

  for instance, if I want a MySQL image  then I search the MySQL and copy
  ```
  docker pull mysql
  ``` 
## Push image
There are the following steps to push the image: 
- Create a docker tag.
- Log into the docker account via CLI mode.
- Push the image.
  
Note: you have to make a unique name for the image, same name image is not acceptable.<br>
You have to create a tag in the same manner as the one given below.
### docker tag

Paste this command in the terminal to tag the image.
```
docker tag image name username/any name
```
### Login via CLI into the docker hub account

Paste this command into the terminal to log in via CLI to the docker hub account.
```
docker login
```
![Screenshot from 2024-08-13 15-50-26](https://github.com/user-attachments/assets/97c62162-0ab7-4d68-aeac-a8942dddb178)

### Push the image

Paste this command in the terminal to push the image on the docker hub.
```
docker push imagename/ar2002/webimage
```
Now, your image will be available on the docker hub all over the world.

# Docker volume
A Docker volume is a storage, that is attached to a container and stores all the data of the container if case a container is stopped or crashes then we can use this volume.
### Check volume

Paste this command in the terminal to check volume.
```
docker volume ls
```
### For help

Paste this command in the terminal for image-related help.
```
docker volume --help
```
 ### Create volume

 Paste this command in the terminal to create volume.
 ```
docker volume create volume name
```
### Check path

Paste this command in the terminal to check the path of volume.
```
docker volume inspect volume name
```
### Copy the path and paste it into the terminal 

Paste this command in the terminal to come inside the volume.
```
cd /var/lib/docker/volumes/myvol/_data
```
### Create some file

Paste this command in the terminal to create some files inside the terminal.
```
touch abc{1..10}
```

### Create a container with an attached volume

Paste this command in the terminal to create  the container with the attached volume.
```
docker container run -it -v vol name:/tmp --name xyz ubuntu /bin/bash
```
- -v stands for volume
### Check whether volume data is available or not

Paste this command in the terminal to check the volume data that we have attached. 
```
cd /mnt/
```

# Docker swarm
Docker Swarm is a tool that allows you to manage workers as an individual manager.
Managers can manage containers, images, and volume at the worker's node.


Docker Swarm is made up of two main components:

- Manager Nodes / Master Nodes.
- Worker Nodes.

![jdbsqluohzrw5ku5l096](https://github.com/user-attachments/assets/41d87518-8eea-4d17-8eb1-f2673a8e5e8a)

Docker swarm needs multiple OS to deploy the service, we can deploy it on any cloud like AWS but it is not open source that's  why basic info is mentioned here about docker swarm.

# Conclusion
Docker is a platform that make easy the process of building, shipping, and running applications in containers. Containers are lightweight, portable, and consistent across different environments.

  # Reference link
- https://docs.docker.com
- https://sematext.com/glossary/docker/
- https://www.cherryservers.com/blog/install-docker-ubuntu-22-04
- https://hub.docker.com/
- https://dev.to/shankarsurya035/how-to-install-and-configure-docker-swarm-on-linux-oe0
