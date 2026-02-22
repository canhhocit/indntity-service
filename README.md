# Identity service
This microservice is responsible for:
* Onboarding users
* Roles and permissions
* Authentication

## Tech stack
* Build tool: maven 3.9.12
* Java: 17
* Framework: Spring boot 3.5.11
* DBMS: MySQL -mysql:lts

## Prerequisites
* Java SDK 17
* A MySQL server

## Start application
`mvn spring-boot:run`

## Build application
`mvn clean package`

## Docker guideline
### Create network:
`docker network create canhhocit-network`

### check: `docker network ls`
### Start MySQL in canhhocit-network
`docker run --network canhhocit-network --name mysql-identity -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d mysql:lts`
  ### create database
docker run --name mysql-identity --network canhhocit-network -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -e MYSQL_DATABASE=spring_02 -e MYSQL_ROOT_HOST=% -d mysql:lts
### Run your application in canhhocit-network

`docker run --name identity-service --network canhhocit-network -p 8080:8080 identity-service:0.0.1`

[`docker run --name identity-service --network canhhocit-network -p 8080:8080 canhhocit/identity-service:0.0.1`]


## Build local
`docker build -t identity-service:0.0.1 .`

# publish with Account docker hub
### B1: Build docker image
docker build -t canhhocit/identity-service:0.0.1 .

### B2: Push docker image to Docker Hub
docker image push canhhocit/identity-service:0.0.1

