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
W: Some index files failed to download. They have been ignored, or old ones used instead

#### Step2: Sometimes the curl package is not installed in the system, To install curl use this command: 
```
 sudo apt-get install curl
```
curl: This is the name of the package you want to install. curl is a command-line tool used to transfer data from a server. It supports various protocols, including HTTP, HTTPS, and FTP.
#### Output:
ankit@ankit:~$ sudo apt-get install curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
curl is already the newest version (7.68.0-1ubuntu2.23).
The following packages were automatically installed and are no longer required:
  bridge-utils gir1.2-goa-1.0 ubuntu-fan
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
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
 ankit@ankit:~$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
ankit@ankit:~$ 
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
ankit@ankit:~$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
[sudo] password for ankit: 

update the local package index once more.
```
sudo apt update
```
#### Output:
ankit@ankit:~$ sudo apt update
Get:1 https://download.docker.com/linux/ubuntu focal InRelease [57.7 kB]
Get:2 https://packages.microsoft.com/repos/code stable InRelease [3,590 B]                                                                                                                     
Get:3 https://download.docker.com/linux/ubuntu focal/stable amd64 Packages [48.8 kB]                   
Hit:4 http://in.archive.ubuntu.com/ubuntu focal InRelease            
Hit:5 http://security.ubuntu.com/ubuntu focal-security InRelease
Get:6 http://in.archive.ubuntu.com/ubuntu focal-updates InRelease [128 kB]
Get:7 https://packages.microsoft.com/repos/code stable/main armhf Packages [18.1 kB]
Get:8 https://packages.microsoft.com/repos/code stable/main arm64 Packages [18.1 kB]
Get:9 https://packages.microsoft.com/repos/code stable/main amd64 Packages [17.9 kB]
Hit:10 http://in.archive.ubuntu.com/ubuntu focal-backports InRelease
Fetched 292 kB in 2s (164 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
43 packages can be upgraded. Run 'apt list --upgradable' to see them.


Now, install Docker Community Edition:
```
sudo apt install docker-ce -y
```
docker-ce: Specifies the package name for Docker Community Edition, which is the free, open-source version of Docker.<br>

-y: Automatically answers "yes" to any prompts that may appear during the installation process.<be>
#### Output:
ankit@ankit:~$ sudo apt install docker-ce -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bridge-utils gir1.2-goa-1.0 ubuntu-fan
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  aufs-tools cgroupfs-mount | cgroup-lite
The following packages will be upgraded:
  docker-ce
1 upgraded, 0 newly installed, 0 to remove and 42 not upgraded.
Need to get 25.3 MB of archives.
After this operation, 9,216 B of additional disk space will be used.
Get:1 https://download.docker.com/linux/ubuntu focal/stable amd64 docker-ce amd64 5:27.1.2-1~ubuntu.20.04~focal [25.3 MB]
Fetched 25.3 MB in 8s (3,120 kB/s)                                                                                                                                                                        
(Reading database ... 185972 files and directories currently installed.)
Preparing to unpack .../docker-ce_5%3a27.1.2-1~ubuntu.20.04~focal_amd64.deb ...
Unpacking docker-ce (5:27.1.2-1~ubuntu.20.04~focal) over (5:27.1.1-1~ubuntu.20.04~focal) ...
Setting up docker-ce (5:27.1.2-1~ubuntu.20.04~focal) ...
Processing triggers for systemd (245.4-4ubuntu3.23) ...

Once you have installed the Docker daemon or service, it should be running. To confirm this, run the command:
```
sudo systemctl status docker
```
#### Output:
ankit@ankit:~$ sudo systemctl status docker
● docker.service - Docker Application Container Engine
     Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2024-08-16 14:51:04 IST; 53s ago
TriggeredBy: ● docker.socket
       Docs: https://docs.docker.com
   Main PID: 5598 (dockerd)
      Tasks: 10
     Memory: 20.6M
     CGroup: /system.slice/docker.service
             └─5598 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock

#### To check whether docker is installed or not

Run this command in the terminal  to check whether docker is installed or not.
```
docker info
```
#### Output:
ankit@ankit:~$ docker info
Client: Docker Engine - Community
 Version:    27.1.1
 Context:    default
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.16.1
    Path:     /usr/libexec/docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v2.29.1
    Path:     /usr/libexec/docker/cli-plugins/docker-compose......
    ........................................
    Insecure Registries:
  127.0.0.0/8
 Live Restore Enabled: false

#### Check the version of Docker :

Run this command in the terminal to check the Docker version.
```
sudo docker --version
```
#### Output:
ankit@ankit:~$ sudo docker --version
Docker version 27.1.1, build 6312585

#### For help in docker

Run this command in the terminal for docker-related command help.
```
docker --help
```
#### Output:
docker --help

Usage:  docker [OPTIONS] COMMAND

A self-sufficient runtime for containers

Common Commands:
  run         Create and run a new container from an image
  exec        Execute a command in a running container
  ps          List containers
  build       Build an image from a Dockerfile
  pull        Download an image from a registry
  push        Upload an image to a registry
..........................
Global Options:
      --config string      Location of client config files (default "/home/ankit/.docker")
  -c, --context string     Name of the context to use to connect to the daemon (overrides DOCKER_HOST env var and default context set with "docker context use")
  -D, --debug              Enable debug mode
  -H, --host list          Daemon socket to connect to
  -l, --log-level string   Set the logging level ("debug", "info", "warn", "error", "fatal") (default "info")
      --tls                Use TLS; implied by --tlsverify
      --tlscacert string   Trust certs signed only by this CA (default "/home/ankit/.docker/ca.pem")
      --tlscert string     Path to TLS certificate file (default "/home/ankit/.docker/cert.pem")
      --tlskey string      Path to TLS key file (default "/home/ankit/.docker/key.pem")
      --tlsverify          Use TLS and verify the remote
  -v, --version            Print version information and quit

Run 'docker COMMAND --help' for more information on a command.

For more help on how to use Docker, head to https://docs.docker.com/go/guides/

# Container

#### To check the container

Run this command in the terminal to check the containers list.
```
docker container ls
```
#### Output:ankit@ankit:~$ docker container ls
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

#### How to make a container
When we run the command on the terminal it will extract data from this website - https://hub.docker.com/
Here, ubuntu is the OS name.
```
docker container run ubuntu
```
#### Output:
ankit@ankit:~$ docker container run ubuntu
ankit@ankit:~$ 

#### Run container in the background only for 60 sec

Run this command in the terminal and the container will run in the background only for 60 sec.
```
docker container run -d ubuntu sleep 60
```
- -d Stands for Detached mode.
- Purpose: Runs the container in the background.
#### Output:
ankit@ankit:~$ docker container run -d ubuntu sleep 60
03fb03684da827318d1aa60b088614dcf6f192df9d27aa4ac255f1ed2bd5fb02
#### Make a running container 

Run this command in the terminal to create a running container.
```
docker container run -d -it ubuntu
```
- -it Stands for Interactive 
- Purpose: Allows you to interact with the container.
#### Output:
ankit@ankit:~$ docker container run -d -it ubuntu
e6bf00e259ee149aa9e5222fccc9f39e9a4db1fcf42be3c588fe772594f048f1
#### See all container
Run this command in the terminal to check the running and stopped container list.
```
docker container ls -a
```
#### Output:
ankit@ankit:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS                     PORTS     NAMES
e6bf00e259ee   ubuntu    "/bin/bash"   2 minutes ago   Up 2 minutes                         lucid_neumann
03fb03684da8   ubuntu    "sleep 60"    3 minutes ago   Exited (0) 2 minutes ago             agitated_jang
3f4680f900ae   ubuntu    "/bin/bash"   5 minutes ago   Exited (0) 5 minutes ago             trusting_bartik

#### Stop the container 

Run this command in the terminal with your container ID and it will stop.
```
docker container stop container id
```
#### Output:
ankit@ankit:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS                        PORTS     NAMES
e6bf00e259ee   ubuntu    "/bin/bash"   5 minutes ago   Exited (137) 22 seconds ago             lucid_neumann
03fb03684da8   ubuntu    "sleep 60"    5 minutes ago   Exited (0) 4 minutes ago                agitated_jang
3f4680f900ae   ubuntu    "/bin/bash"   7 minutes ago   Exited (0) 7 minutes ago                trusting_bartik
57eb84a45887   ubuntu    "/bin/bash"   8 days ago      Exited (137) 8 days ago                 myvolcontainer1
ankit@ankit:~$ docker container stop e6bf00e259ee
e6bf00e259ee
ankit@ankit:~$ docker container stop 03
03
ankit@ankit:~$ docker container stop 3
3
ankit@ankit:~$ docker container stop myvol
Error response from daemon: No such container: myvol
ankit@ankit:~$ docker container stop myvolcontainer1
myvolcontainer1
ankit@ankit:~$ 

#### Start the container

Run this command in the terminal with your container ID and it will start.
```
docker container start container id
```
#### Output:
ankit@ankit:~$ docker container start 57
57
ankit@ankit:~$ docker container start e6
e6

#### Restart the container

Run this command in the terminal with your container ID and the running container will restart(stop the running container and then again start container).
```
docker container restart container id
```
#### Output:
ankit@ankit:~$ docker container start e6
e6
ankit@ankit:~$ docker container restart e6
e6
#### Delete a stopped container

Run this command in the terminal with your container ID and it will deleted or removed.
```
docker container rm container id
```
#### Output:
ankit@ankit:~$ docker container rm 03
03
ankit@ankit:~$ 
#### Delete a running container
Run this command in the terminal with your container ID and your running container will be deleted forcefully (-f).
```
docker container rm container id -f
```
#### Output:
ankit@ankit:~$ docker container rm container 3f -f
Error response from daemon: No such container: container
3f
ankit@ankit:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
ankit@ankit:~$ 

# Apache server 
Apache is a web server tool that accepts visitors' HTTP requests and sends them back the requested information in the form of web pages.

#### Create and come inside the container

Run this command in the terminal, and you will come inside the new container.
```
docker container run -it ubuntu /bin/bash
```
#### Output:
ankit@ankit:~$ docker container run -it ubuntu /bin/bash
root@5a1089d3971e:/# 
#### Exit from the container

Press this command in the terminal and you will exit from the container.
```
ctrl+p 
```
```
ctrl+q
```
#### Output:
ankit@ankit:~$ docker container run -it ubuntu /bin/bash
root@5a1089d3971e:/# ankit@ankit:~$ 

#### Come inside the container

Run this command in the terminal, and you will come inside the container.
```
docker container attach id
```
#### Output:
ankit@ankit:~$ docker container attach 5a
root@5a1089d3971e:/# 
#### Update the container

Run this command in the terminal, inside the container, and the container will be updated.
```
apt-get update
```
#### Output:
ankit@ankit:~$ docker container attach 5a
root@5a1089d3971e:/# apt-get update
Get:1 http://archive.ubuntu.com/ubuntu noble InRelease [256 kB]
Get:2 http://security.ubuntu.com/ubuntu noble-security InRelease [126 kB]
Get:3 http://security.ubuntu.com/ubuntu noble-security/multiverse amd64 Packages [12.7 kB]
Get:4 http://archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
Get:5 http://security.ubuntu.com/ubuntu noble-security/restricted amd64 Packages [309 kB]
Get:6 http://archive.ubuntu.com/ubuntu noble-backports InRelease [126 kB]
Get:7 http://archive.ubuntu.com/ubuntu noble/universe amd64 Packages [19.3 MB]
Get:8 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Packages [334 kB]
Get:9 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages [368 kB]    
Get:10 http://archive.ubuntu.com/ubuntu noble/restricted amd64 Packages [117 kB]                                                                                                                          
Get:11 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages [1808 kB]                                                                                                                               
Get:12 http://archive.ubuntu.com/ubuntu noble/multiverse amd64 Packages [331 kB]                                                                                                                          
Get:13 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages [438 kB]                                                                                                                        
Get:14 http://archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Packages [309 kB]                                                                                                                  
Get:15 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages [430 kB]                                                                                                                    
Get:16 http://archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Packages [16.9 kB]                                                                                                                 
Get:17 http://archive.ubuntu.com/ubuntu noble-backports/universe amd64 Packages [11.5 kB]                                                                                                                 
Fetched 24.4 MB in 9s (2664 kB/s)                                                                                                                                                                         
Reading package lists... Done
root@5a1089d3971e:/# 

#### Install  apache

Run this command in the terminal and Apache will install it into your container.
```
apt-get install apache2
```
#### Output:
root@5a1089d3971e:/# apt-get install apache2
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
..................
.................
Processing triggers for ca-certificates (20240203) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.
root@5a1089d3971e:/# 

Now come inside the folder:
```
cd /var/www/html/
```
#### Output:
root@5a1089d3971e:/# cd /var/www/html/
root@5a1089d3971e:/var/www/html# 

Add welcome to keen&able.
```
echo "Welcome to keen&able" >index.html
```
#### Output:
root@5a1089d3971e:/var/www/html# echo "Welcome to keen&able" >index.html
root@5a1089d3971e:/var/www/html# 
#### Start the service
Now, come outside from the folder
```
cd
```
Run this command in the terminal to restart the Apache service.
```
service apache2 start
```
#### Output:
root@5a1089d3971e:/var/www/html# cd
root@5a1089d3971e:~# service apache2 start
 * Starting Apache httpd web server apache2                                                                                                                                                                 * 
root@5a1089d3971e:~# 
#### Check the IP add
Now, come outside from the container and press ctrl+p,ctrl+q
Run this command in the terminal to check the container's IP. 
```
docker container inspect id
```
- ip add a mention in the 12th line from the last
#### Output:
ankit@ankit:~$ docker container inspect 5a
[
    {
        "Id": "5a1089d3971e782268250234950d1e5f0746ce3c75cf5471fedf05a1d1ead95f",
        "Created": "2024-08-16T09:51:47.980820976Z",
.....................

 "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null,
                    "NetworkID": "f9abe4117bf7811604c3ab76464eff541bc955499e0daf31f26b531ce44d9083",
                    "EndpointID": "fff411a1618f9accb0f4f3dc99dbd6717860bc4c676ead1bf80758ce57c575dd",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "DNSNames": null
                }
            }
        }
    }
]
ankit@ankit:~$ 
#### Check the output

Run this command in the terminal to check the Apache server output on the terminal.
```
curl IP
```
#### Output:
ankit@ankit:~$ curl 172.17.0.2
Welcome to keen&able
ankit@ankit:~$ 
#### Check how much space the container has used

Run this command in the terminal with the container ID to check the space used by the container.
```
docker container stats id
```
#### Output:
CONTAINER ID   NAME                 CPU %     MEM USAGE / LIMIT     MEM %     NET I/O        BLOCK I/O         PIDS
5a1089d3971e   magical_williamson   0.01%     83.43MiB / 7.541GiB   1.08%     54.6MB / 1MB   35.8MB / 73.5MB   56

# Container port mapping
In Docker, port mapping is the process of making a specific port of a container accessible from the host machine or network. This allows services running inside the container to be accessed externally.
#### Create a container with port no 

Run this command in the terminal to create the container with changed port no.
```
docker container run -it -p 3600:80 ubuntu /bin/bash
```
#### Output:
ankit@ankit:~$ docker container run -it -p 3600:80 ubuntu /bin/bash
root@71a4d536f8c5:/# 
#### Update the container

Run this command in the terminal, inside the container, and the container will be updated.
```
apt-get update
```
#### Output:
root@e2798e258743:/# apt-get install apache2
Reading package lists... Done
Building dependency tree... Done
....................
.............
Get:16 http://archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Packages [16.9 kB]                                                                                                                 
Get:17 http://archive.ubuntu.com/ubuntu noble-backports/universe amd64 Packages [11.5 kB]                                                                                                                 
Fetched 24.4 MB in 1min 24s (292 kB/s)                                                                                                                                                                    
Reading package lists... Done

#### Install apache

Run this command in the terminal to install Apache.
```
apt-get install apache2
```
#### Output:
root@e2798e258743:/# apt-get install apache2
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
........
........
Processing triggers for libc-bin (2.39-0ubuntu8.2) ...
Processing triggers for ca-certificates (20240203) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.
root@e2798e258743:/# 

### Now come inside the folder:
```
cd /var/www/html/
```
#### Output:
root@e2798e258743:/# cd /var/www/html/
root@e2798e258743:/var/www/html# 
### Add welcome to keen&able.
```
echo "Welcome to keen&able" >index.html
```
#### Output:
root@e2798e258743:/var/www/html# echo "Welcome to keen&able" >index.html
root@e2798e258743:/var/www/html# 

#### Start the service

Run this command in the terminal to start the service.
```
service apache2 start
```
#### Output:
root@e2798e258743:~# service apache2 start
 * Starting Apache httpd web server apache2                                                                                                                                                                 * 
root@e2798e258743:~# 
#### Now check your system ip in another tab
Run this command in another terminal to check the IP
```
ifconfig
```
#### Output:
wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.29  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::a75e:9d67:4cec:8dd2  prefixlen 64  scopeid 0x20<link>

#### Paste this on the web browser
Run the IP with port no, and then data will be visible on the webserver.
```
ip add:3600
```
#### Output:
![Screenshot from 2024-08-16 17-50-24](https://github.com/user-attachments/assets/1c1e6926-c7c3-439d-9669-6f9a325abae5)

## Change container name

Run this command in the terminal to change the container name.
```
docker container rename id new name
```
#### Output:
ankit@ankit:~$ docker container rename e2  mycont1
ankit@ankit:~$ docker container ls
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS                                   NAMES
e2798e258743   ubuntu    "/bin/bash"   19 minutes ago   Up 19 minutes   0.0.0.0:3600->80/tcp, :::3600->80/tcp   mycont1
5a1089d3971e   ubuntu    "/bin/bash"   3 hours ago      Up 3 hours                                              magical_williamson

## Pause the container

Run this command in the terminal to pause the container.
```
docker container pause id/name
```
#### Output:
ankit@ankit:~$ docker container ls
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                   PORTS                                   NAMES
e2798e258743   ubuntu    "/bin/bash"   20 minutes ago   Up 20 minutes (Paused)   0.0.0.0:3600->80/tcp, :::3600->80/tcp   mycont1
5a1089d3971e   ubuntu    "/bin/bash"   3 hours ago      Up 3 hours                                                       magical_williamson
ankit@ankit:~$ 

## Unpause the container
Run this command in the terminal to unpause the container.
```
docker container unpause id/name
```
#### Output:
ankit@ankit:~$ docker container unpause e2
e2
ankit@ankit:~$ docker container ls
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS                                   NAMES
e2798e258743   ubuntu    "/bin/bash"   21 minutes ago   Up 21 minutes   0.0.0.0:3600->80/tcp, :::3600->80/tcp   mycont1
5a1089d3971e   ubuntu    "/bin/bash"   3 hours ago      Up 3 hours                                              magical_williamson
# Import the data from the system 

Run this command in the terminal to copy data from the system and paste it into the container's location.
```
docker container cp filename id:/location
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
