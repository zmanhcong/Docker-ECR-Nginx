Deploy Docker in AWS/ECS

1. Install EC2<br>
* #This is Data use.
* >#!/bin/bash<br>
* >yum update -y<br>
* >yum install -y docker<br>
* >service docker start<br>
* >chkconfig docker on<br>
* >curl -L "https://github.com/docker/compose/releases/download/1.11.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose<br>
* >chmod +x /usr/local/bin/docker-compose<br>



$ mkdir nginx<br>
$ cd nginx<br>
$ vi Dockerfile<br>
FROM nginx<br>
COPY html /usr/share/nginx/html<br>


$ mkdir html<br>
$ vi html/index.html<br>
<html><br>
<head><title>docker-ecr</title></head><br>
<body><h1>Xin chao docker-ecr</h1></body><br>
</html><br>


*$docker build -t [Image Name]:tag .<br>
	->docker build -t docker-ecr:v1 .<br>

*- AWS ECR Login<br>
aws ecr get-login --no-include-email --region ap-northeast-1<br>


*- Create repository on AWS/ECR(Amazon Elastic Container Registry)<br>
aws ecr create-repository --repository-name [Repository Name] --region ap-northeast-1<br>
->aws ecr create-repository --repository-name docker-ecr --region ap-northeast-1<br>

<br>
*- Create tag version docker image<br>
docker tag [Image Name]:tag [Repository ULR] created below]<br>
->docker tag docker-ecr:v1 310045062335.dkr.ecr.ap-northeast-1.amazonaws.com/docker-ecr<br>

*- Push in  AWS/ECR<br>
docker push [Repository ULR]<br>
->docker push 251123607109.dkr.ecr.ap-northeast-1.amazonaws.com/docker-ecr<br>

- Create Task trên AWC/ECS<br>
- Create Clusters on AWC/ECS<br>
- Create Service on AWC/ECS<br>






*Batch delete commands<br>
        docker stop $(docker ps -a -q)<br>
        docker rm $(docker ps -a -q)<br>
        docker rmi -f $(docker images -a -q)<br>
