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
• Run a container httpd with name apache and attach a volume to the container

```bash 
sudo docker volume create --lab1volume
```
```bash
sudo docker run -it  -v lab1volume:/var/www/html --name nginx5 nginx bash
```
```bash 
touch ahmed.html
```bash
sudo docker rm nginx5
```
```bash
sudo docker run -it  -v lab1volume:/var/www/html -p 8090:80  --name nginx13 nginx bash
```
-----------------------------------------------------
### Problem 4 
• Run the image httpd again without attaching any
volumes

```bash 
sudo docker run -it --name nginx3 nginx bash
```bash
 sudo docker commit 4ac6
```
```bash 
sudo docker commit 4ac6
```
```bash 
sudo docker build .
```
------------------------------
### Problem 5 

• Create a volume called mysql

```bash
sudo docker run -d -p 80:3306 -e MYSQL_ROOT_PASSWORD="Password" -v mysql_data:/var/lib/mysql  --name app-database mysql
```

