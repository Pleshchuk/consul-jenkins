## Tested OS Platform
This project was tested on Windows OS

## Usage
In the root of repository you can see docker-compose.yml file. 

To start project it is enough to go to repository root folder and execute ```docker-compose up```

It will build and start 3 docker containers on your localhost:

consul-server

consul-client

jenkins-server

## UI access
To access consul-server UI just use http://localhost:8500 on your local PC

To access jenkins-server UI use http://localhost:8080 on your local PC

## Jenkins Server
Jenkins server will be started with preconfigured user and two Jenins jobs. 

The username and password can be set inside docker-compose.yml file. There are two variables JENKINS_USERNAME and JENKINS_USER_PASSWORD with predefined values (jenkins as default). You can change value of these variables to changes username and password.

After login to Jenkins UI you will see two Jenkins jobs:

```consul-service-build``` - builds docker image for consul-service by using source code from https://github.com/Pleshchuk/python-consul-service repository

```consul-service-deploy``` - runs docker container by using docker image which was built by consul-service-build jenkins job. It's packaged with predefined default parameter for image name but you can change it before running jenkins job.



