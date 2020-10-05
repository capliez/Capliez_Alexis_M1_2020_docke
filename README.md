# DOCKER

### Objectives

Deployment of a Rest API with Docker in order to be able to integrate it in a continuous integration and development system

### Prerequisites

What you need to use it:
  * GitHub
  * Docker

### Installation

Step to install:
  1. ``` git clone https://github.com/capliez/Capliez_Alexis_M1_2020_docke.git ```
  2. ``` docker-compose up --build ```
  3. Go to ``` http://localhost:3000/ ```

### How to use the application

You can create an account by registering in the registration section with your email address and password.

## DOCKER configuration file

- Frontend : front web app components public 
- Backend : node API 
- docker-compose.yaml : Allows to build an image and its environment
- Dockerfile : Allows to build an image but also to execute commands

***frontend/Dockerfile***
````
FROM node:10
WORKDIR /frontend
COPY . /frontend/
RUN npm install
EXPOSE 3000
CMD ["npm", "start"]
````


***backend/Dockerfile***
````
FROM node:10
WORKDIR /backend
COPY . /backend/
RUN npm install
EXPOSE 8080
CMD ["npm", "start"]
````

***docker-compose.yml***
````
version: "3"

services:
  backend:
    container_name: server
    build: ./backend
    restart: always
    ports:
      - "8080:8080"
    depends_on:
      - mongodb
      
  mongodb:
    image: mongo:latest
    container_name: mongodb
    expose: 
        - 27017
    ports:
      - 27017:27017

  frontend:
    container_name: client
    build: ./frontend
    ports:
      - "3000:3000"
````

 
 

