# DOCKER

# API MERN STACK - DOCKER :whale:

### Prerequisites

What you need to use it:
  * GitHub
  * Docker

### Installation

Step to install:
  1. ``` git clone https://github.com/capliez/Capliez_Alexis_M1_2020_docke.git ```
  2. ``` docker-compose up --build ```
  3. Go to ``` http://localhost:3000/ ```

### Using the application

You can create an account by registering in the registration section.

## SETUP

#### DOCKER SETUP
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

 
 

