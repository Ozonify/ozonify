# Deployment Guide

This deployment procedure is made for purpose of deploying the apps for development server only.

Currently, you need 4 projects namely Indozonify-web, common-lib, auth-service and payload-decoder.

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

## payload-decoder
1. clone the project
2. zip and scp the project folder
3. in the project folder, execute `docker build -t payload_decoder .`
4. then execute `docker run -p 5000:5000 -t -d payload_decoder`
