# Docker-ITI
## lab 1

### Problem 1
-------------------
• Run the container hello-world

``` bash
sudo docker run hello-world
````
--------------------
• Check the container status

``` bash
sudo docker ps -a 
```
- status: exited
-------------------------
• Start the stopped container

```bash 
sudo docker start <conainer-name>
```
------------------------------
• Remove the container

```bash
sudo docker rm f61f
``` 
--------------------------------
• Remove the image
```bash
sudo docker image rm <Image-Name>
``` 
------------------------------
### Problem 2 
-------------------
• Run container centos or ubuntu in an interactive mode

```bash 
sudo docker run -i ubuntu 
```
----------------
• Run the following command in the container “echo docker ”

```bash 
echo docker
```
-----------------
• Open a bash shell in the container and touch a file named hello-docker

 ```bash 
 sudo docker run -it ubuntu 
 touch hello-docker 
```
------------------
• Stop the container and remove it. Write your
comment about the file hello-docker

```bash 
sudo docker rm 98eff
```
- the file will be deleted with the container
---------------------------------------------
• Remove all stopped containers
```bash
sudo docker rm $(sudo docker ps -aq -f status=exited )
```
-----------------------------------------------------------
### Problem 3 
• Run a container httpd with name apache and
attach a volume to the container

```bash

```
 


