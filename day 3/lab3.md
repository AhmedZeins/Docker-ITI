## lab 3 

### Problem 1 
- Create Docker copmose yaml fiiiile 
```yml
version: '3.8'

services:
  app:
    container_name: lab2c3
    image: la4:2.0
    ports:
      - 8089:80
```
-------------------------------------
### Problem 2 
- Create a Dockerfile

```Dockerfile
FROM python:3.7-alpine
WORKDIR /code
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0
RUN apk add --no-cache gcc musl-dev linux-headers
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt
EXPOSE 5000
COPY . .
CMD ["flask", "run"]
```
-Build and run your app:

```bash
sudo docker build -t py2:1.0 .
```
-Define services in a Compose file

```yml
version: "3.9"
services:
  web:
    image: py2:1.0
    ports:
      - "8000:5000"
  redis:
    image: "redis:alpine"
```
- Run your app with Docker Compose

```bash
sudo docker compose up
```