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
 
 Run this command in the terminal  to check the version.
 ```
 lsb_release -a
```
- lsb_release: Stands for "Linux Standard Base release." It is a command-line tool that provides information about the Linux distribution's release.
- -a: This option stands for "all." It instructs the command to display all available information.
#### Output:
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.6 LTS
Release:	20.04
Codename:	focal
### RAM 
At least we have 2 GB of RAM in our system to run docker.
#### How to check the RAM?

Run this command in the terminal  to check the RAM.
 ```
 free -h
```
- free: This command displays the total amount of free and used physical memory (RAM) and swap memory in the system, as well as the buffers and caches used by the kernel.

- -h: This option stands for "human-readable." It modifies the output to be in a format that is easier to read, typically using units like KB, MB, or GB instead of displaying the memory in bytes.
#### Output:
ankit@ankit:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:          7.5Gi       2.5Gi       3.2Gi       463Mi       1.9Gi       4.3Gi
Swap:         2.0Gi          0B       2.0Gi

#### Step 1. Update system by using the following command :

Run this command in the terminal to update your system.
```
 sudo apt-get update
```
- sudo: This prefix stands for "superuser do." It allows you to run commands with elevated privileges (as an administrator) that may be required for certain operations, like updating the system.

- apt-get: APT: Stands for Advanced Package Tool, a command-line tool for handling packages. It allows you to install, update, and remove software packages.

- update: This subcommand tells apt-get to download the latest package lists from the repositories specified in your system's configuration files (typically found in /etc/apt/sources.list)
#### Output:

#### Step2: Sometimes the curl package is not installed in the system, To install curl use this command: 
```
 sudo apt-get install curl
```
curl: This is the name of the package you want to install. curl is a command-line tool used to transfer data from a server. It supports various protocols, including HTTP, HTTPS, and FTP.
#### Output:
ankit@ankit:~$ sudo apt-get update
[sudo] password for ankit: 
Get:1 https://download.docker.com/linux/ubuntu focal InRelease [57.7 kB]                                                                                                                                  
Get:2 https://packages.microsoft.com/repos/code stable InRelease [3,590 B]                                                                                                                                
Hit:3 http://in.archive.ubuntu.com/ubuntu focal InRelease                                                                         
Err:1 https://download.docker.com/linux/ubuntu focal InRelease             
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7EA0A9C3F273FCD8
Get:4 http://in.archive.ubuntu.com/ubuntu focal-updates InRelease [128 kB]
Get:5 https://packages.microsoft.com/repos/code stable/main arm64 Packages [17.9 kB]
Get:6 http://security.ubuntu.com/ubuntu focal-security InRelease [128 kB]                 
Get:7 https://packages.microsoft.com/repos/code stable/main amd64 Packages [17.8 kB]
Get:8 https://packages.microsoft.com/repos/code stable/main armhf Packages [18.0 kB]                             
Hit:9 http://in.archive.ubuntu.com/ubuntu focal-backports InRelease                                                          
Get:10 http://in.archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [1,017 kB]
Get:11 http://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [3,496 kB]
Get:12 http://security.ubuntu.com/ubuntu focal-security/main i386 Packages [797 kB]
Get:13 http://in.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [543 kB]
Get:14 http://in.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [17.7 kB]    
Get:15 http://in.archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [801 kB]           
Get:16 http://in.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [1,219 kB]
Get:17 http://in.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [294 kB]   
Get:18 http://in.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [27.8 kB]
Get:19 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [3,126 kB]            
Get:20 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [464 kB]
Get:21 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [14.2 kB]
Get:22 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [999 kB]
Get:23 http://security.ubuntu.com/ubuntu focal-security/universe i386 Packages [674 kB]
Get:24 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [212 kB]
Get:25 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [21.0 kB]
Fetched 14.1 MB in 6s (2,288 kB/s)                                                                                                                                                                        
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://download.docker.com/linux/ubuntu focal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7EA0A9C3F273FCD8
W: Failed to fetch https://download.docker.com/linux/ubuntu/dists/focal/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7EA0A9C3F273FCD8
W: Some index files failed to download. They have been ignored, or old ones used instead.
#### Step 3. Install the dependency packages to install Docker.

Run this command into the terminal to install the dependency packages.
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
- sudo: Runs the command with superuser or administrator privileges.

- apt install: Installs the specified packages.

- apt-transport-https: Enables apt to retrieve packages over the HTTPS protocol, which is more secure than HTTP.

- ca-certificates: Installs digital certificates to ensure the system can verify the authenticity of HTTPS connections.

- curl: A command-line tool for transferring data using various protocols, such as HTTP, HTTPS, and FTP.

- software-properties-common: Provides tools to manage software repositories, including adding new ones.
#### Output:
ankit@ankit:~$ sudo apt install apt-transport-https ca-certificates curl software-properties-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ca-certificates is already the newest version (20230311ubuntu0.20.04.1).
curl is already the newest version (7.68.0-1ubuntu2.23).
software-properties-common is already the newest version (0.99.9.12).
apt-transport-https is already the newest version (2.0.10).
The following packages were automatically installed and are no longer required:
  bridge-utils gir1.2-goa-1.0 ubuntu-fan
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
#### Step 4. Install Docker

Run this command in the terminal  to install docker.
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
 #### Output:
 
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
#### Output:

update the local package index once more.
```
sudo apt update
```
#### Output:

Now, install Docker Community Edition:
```
sudo apt install docker-ce -y
```
docker-ce: Specifies the package name for Docker Community Edition, which is the free, open-source version of Docker.<br>

-y: Automatically answers "yes" to any prompts that may appear during the installation process.<be>
#### Output:

Once you have installed the Docker daemon or service, it should be running. To confirm this, run the command:
```
sudo systemctl status docker
```
![Screenshot from 2024-08-13 15-45-30(1)](https://github.com/user-attachments/assets/adf0f39e-dbff-432e-b090-ff8abfcf263f)
#### Output:

#### To check whether docker is installed or not

Run this command in the terminal  to check whether docker is installed or not.
```
docker info
```
#### Output:

#### Check the version of Docker :

Run this command in the terminal to check the Docker version.
```
sudo docker --version
```
#### Output:

#### For help in docker

Run this command in the terminal for docker-related command help.
```
docker --help
```
#### Output:
# Container

#### To check the container

Run this command in the terminal to check the containers list.
```
docker container ls
```
#### Output:
#### How to make a container
When we run the command on the terminal it will extract data from this website - https://hub.docker.com/
Here, ubuntu is the OS name.
```
docker container run ubuntu
```
#### See all container
Run this command in the terminal to check the running and stopped container list.
```
docker container ls -a
```
#### Output:

#### Run container in the background only for 60 sec

Run this command in the terminal and the container will run in the background only for 60 sec.
```
docker container run -d ubuntu sleep 60
```
- -d Stands for Detached mode.
- Purpose: Runs the container in the background.
#### Output:

#### Make a running container 

Run this command in the terminal to create a running container.
```
docker container run -d -it ubuntu
```
- -it Stands for Interactive 
- Purpose: Allows you to interact with the container.
#### Output:

#### Stop the container 

Run this command in the terminal with your container ID and it will stop.
```
docker container stop container id
```
#### Output:

#### Start the container

Run this command in the terminal with your container ID and it will start.
```
docker container start container id
```
#### Output:

#### Restart the container

Run this command in the terminal with your container ID and the running container will restart.
```
docker container restart container id
```
#### Output:
#### Delete a stopped container

Run this command in the terminal with your container ID and it will deleted or removed.
```
docker container rm container id
```
#### Output:
#### Delete a running container
Run this command in the terminal with your container ID and your running container will be deleted forcefully (-f).
```
docker container rm container id -f
```
#### Output:
# Apache server 
Apache is a web server tool that accepts visitors' HTTP requests and sends them back the requested information in the form of web pages.

#### Create and come inside the container

Run this command in the terminal, and you will come inside the new container.
```
docker container run -it ubuntu /bin/bash
```
#### Output:
#### Exit from the container

Press this command in the terminal and you will exit from the container.
```
ctrl+p 
```
```
ctrl+q
```
#### Output:
#### Come inside the container

Run this command in the terminal, and you will come inside the container.
```
docker container attach id
```
#### Output:

#### Update the container

Run this command in the terminal inside the container, and the container will be updated.
```
apt-get update
```
#### Output:

#### Install  apache

Run this command in the terminal and Apache will install it into your container.
```
apt-get install apache2
```
#### Output:

Now come inside the folder:
```
cd /var/www/html/
```
Add welcome to keen&able.
```
echo "Welcome to keen&able" >index.html
```
#### Output:
#### Start the service

Run this command in the terminal to restart the Apache service.
```
service apache2 start
```
#### Output:

#### Check the IP add

Run this command in the terminal to check the container's IP. 
```
docker container inspect id
```
- ip add a mention in the 12th line from the last
#### Output:

#### Check the output

Run this command in the terminal to check the Apache server output on the terminal.
```
curl IP
```
#### Output:

#### Check how much space the container has used

Run this command in the terminal with the container ID to check the space used by the container.
```
docker container stats id
```
#### Output:
# Container port mapping
In Docker, port mapping is the process of making a specific port of a container accessible from the host machine or network. This allows services running inside the container to be accessed externally.
#### Create a container with port no 

Run this command in the terminal to create the container with changed port no.
```
docker container run -it -p 3600:80 ubuntu /bin/bash
```
#### Output:
#### Install apache

Run this command in the terminal to install Apache.
```
apt-get install apache2
```
#### Output:
Now come inside the folder:
```
cd /var/www/html/
```
#### Output:
Add welcome to keen&able.
```
echo "Welcome to keen&able" >index.html
```
#### Output:
#### Start the service

Run this command in the terminal to start the service.
```
service apache2 start
```
#### Output:
#### Now check your system ip in another tab
Run this command in another terminal to check the IP
```
ifconfig
```
#### Output:
#### Paste this on the web browser
Run the IP with port no, and then data will be visible on the webserver.
```
ip add:3600
```
#### Output:
## Change container name

Run this command in the terminal to change the container name.
```
docker container rename id new name
```
#### Output:
## Pause the container

Run this command in the terminal to pause the container.
```
docker container pause id/name
```
## Unpause the container
Run this command in the terminal to unpause the container.
```
docker container unpause id/name
```
#### Output:
# Import the data from the system 

Run this command in the terminal to copy data from the system and paste it into the container's location.
```
docker container cp docker.svg id:/location
```
#### Output:
# Docker image
Docker images are used to create containers, which are instances of these images running in an isolated environment.

#### Export and import the container

Run this command in the terminal to export the container data into a file.
```
docker container export ID>file name
```
#### Output:
#### Create image

Run this command in the terminal to import and make an image using the container's file.
```
docker image import filename image name
```
#### Output:
#### Create a container with an image

Run this command in the terminal to create a container with an image.
```
docker container run -it image name /bin/bash
```
#### Output:
#### Create an image directly
In the last two commands firstly we have to export the data in a file and then convert it to a docker image.
Now, we can create images directly 
```
docker container commit id image name
```
#### Output:
#### To check

Run this command in the terminal to  check the image list.
```
docker image ls
```
#### Output:
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

Run this command in the terminal to tag the image.
```
docker tag image name username/any name
```
#### Output:
### Login via CLI into the docker hub account

Run this command into the terminal to log in via CLI to the docker hub account.
```
docker login
```
#### Output:
![Screenshot from 2024-08-13 15-50-26](https://github.com/user-attachments/assets/97c62162-0ab7-4d68-aeac-a8942dddb178)

### Push the image

Run this command in the terminal to push the image on the docker hub.
```
docker push imagename/ar2002/webimage
```
#### Output:
Now, your image will be available on the docker hub all over the world.

# Docker volume
A Docker volume is a storage, that is attached to a container and stores all the data of the container if case a container is stopped or crashes then we can use this volume.
### Check volume

Run this command in the terminal to check volume.
```
docker volume ls
```
#### Output:
### For help

Run this command in the terminal for image-related help.
```
docker volume --help
```
#### Output:
 ### Create volume

Run this command in the terminal to create volume.
 ```
docker volume create volume name
```
#### Output:
### Check path

Run this command in the terminal to check the path of volume.
```
docker volume inspect volume name
```
#### Output:
### Copy the path and paste it into the terminal 

Run this command in the terminal to come inside the volume.
```
cd /var/lib/docker/volumes/myvol/_data
```
#### Output:
### Create some file

Run this command in the terminal to create some files inside the terminal.
```
touch abc{1..10}
```
#### Output:
### Create a container with an attached volume

Run this command in the terminal to create  the container with the attached volume.
```
docker container run -it -v vol name:/tmp --name xyz ubuntu /bin/bash
```
- -v stands for volume
- #### Output:
### Check whether volume data is available or not

Run this command in the terminal to check the volume data that we have attached. 
```
cd /mnt/
```
#### Output:
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
