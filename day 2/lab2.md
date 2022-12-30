## lap 2
### Problem 1 
• P1: Create your own nginx docker image based on ubuntu
```Dockerfile
FROM ubuntu:23.04
RUN  apt-get update
RUN  apt-get install nginx -y
ADD index.html /var/www/html/
ADD index.tar /var/www/html/
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

------------
### Problem 2 
• Single Stage 
```Dockerfile
FROM node:alpine3.16
WORKDIR /app
COPY package*.json ./
RUN npm install 
COPY . .
EXPOSE 3000 
CMD [ "npm" , "start" ]
```
- then we run this command 
```bash 
sudo docker build -t la1:2.0 .
```
• multistage 
```Dockerfile
#build stage 
FROM node:alpine3.16 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install 
COPY . .
EXPOSE 3000 
RUN npm run build 

# deploy stage 

FROM nginx:alpine
COPY --from=build  /app/build /usr/share/nginx/html
EXPOSE 80
ENTRYPOINT [ "nginx", "-g", "daemon off;" ]
```
- then we run this commands 
```bash 
sudo docker build -t la2:2.0 .
```
----------------
### Problem 3 
- ipvlan: IPvlan networks give users total control over both IPv4 and IPv6 addressing. The VLAN driver builds on top of that in giving operators complete control of layer 2 VLAN tagging and even IPvlan L3 routing for users interested in underlay network integration. 

- macvlan: Macvlan networks allow you to assign a MAC address to a container, making it appear as a physical device on your network. The Docker daemon routes traffic to containers by their MAC addresses. Using the macvlan driver is sometimes the best choice when dealing with legacy applications that expect to be directly connected to the physical network, rather than routed through the Docker host’s network stack.

- network plugins: You can install and use third-party network plugins with Docker. These plugins are available from Docker Hub or from third-party vendors.
------------------------------------------------------------------------------
### Problem 4
1- Frist create our containers 
```bash 
 sudo docker run -d -t -p 8082:80 --name ubuntu3 ubuntu
 sudo docker run -d -t -p 8084:80 --name ubuntu5 ubuntu
```
 2- Create new Network 
```bash
 sudo docker network create lab2
```
 3- Check if your containers are part of the new network
```bash
 sudo docker network inspect lab2
```
4- Connect the containers to the network
```bash
sudo docker network connect lab2 ubuntu5
sudo docker network connect lab2 ubuntu5
```
5- Test the connection
```bash
sudo docker exec -it ubuntu3 ping ubuntu5
```
• Side note:

-if you had this error:

-OCI runtime exec failed: exec failed: unable to start container process: exec: "ping": executable file not found in $PATH: unknown

-just do this steps: 
 • frist access the terminal in both containers by this command 
 ```bash
 sudo docker exec -it ubuntu5 /bin/bash
 ```
 then in both containers run this two command :
 ```bash
 apt-get update
 apt-get install inetutils-ping
 ```