# Deployment Guide

This deployment procedure is made for purpose of deploying the apps for development server only.

Currently, you need all of the projects below for the system to work properly.

## indozonify-web
1. clone the project
2. execute `ng build  --prod`
3. execute `zip dist.zip dist/`
4. scp dist.zip to server
5. in the ‘/root’ directory, execute `./deploy_web.sh`

## common-lib
This project is a dependency for auth-service project. You just need to build this project for it to be deployed to your local .m2 directory.

1. clone the project
2. execute `mvn clean install`

## auth-service
1. clone the project
2. make sure that commons-lib is already installed in the local .m2 directory
3. execute `mvn clean package`
4. scp target/auth-service.jar to server
5. in the ‘/root’ directory, execute `java -jar auth-service.jar`

## master-data
1. clone the project
2. execute `mvn clean package`
3. scp target/master-data.jar to server
4. in the ‘/root’ directory, execute `java -jar master-data.jar`

## device-service
1. clone the project
2. execute `mvn clean package`
3. scp target/device-service.jar to server
4. in the ‘/root’ directory, execute `java -jar device-service.jar`

## uplink-message-service
1. clone the project
2. execute `docker build -t uplink-message-service .`
3. execute `docker run -p 8000:8000 -t -d uplink-message-service`
