1. Tạo IAM user
"Create new group, has the following permision:
1. AmazonEC2ContainerRegistryFullAccess
2. AmazonECS_FullAccess"

2. Cài EC2 có usedata.
3. Cấu hình AWS CLI
aws configure
input data key..vv..v
Check by cmd: aws configuration list

4. Tạo docker image
cd /home/
mkdir nginx
cd ndinx
$ vi Dockerfile
FROM nginx
COPY html /usr/share/nginx/html

$ mkdir html
$ vi html/index.html
<html>
<head><title>Tin hoc that la don gian</title></head>
<body><h1>Xin chao tin hoc that la don gian</h1></body>
</html>
for exit:  ":wq"

$docker build -t [Image Name]:tag .
        ->docker build -t tinhocthatladongian:v1 .
Check: docker images


- AWS ECR Login
aws ecr get-login --no-include-email --region eu-west-2


- Tạo repository lên AWS/ECR(Amazon Elastic Container Registry)
aws ecr create-repository --repository-name [Repository Name] --region eu-west-2
->aws ecr create-repository --repository-name tinhocthatladongian --region eu-west-2


- Tạo tag version docker image
docker tag [Image Name]:tag [Repository ULR] đã tạo ra ở bước trên]
->docker tag tinhocthatladongian:v1 251123607109.dkr.ecr.eu-west-2.amazonaws.com/tinhocthatladongian

- Push lên AWS/ECR
docker push [Repository ULR]
->docker push 251123607109.dkr.ecr.eu-west-2.amazonaws.com/tinhocthatladongian
For check pushed?? -> ECS -> Repository -> check
     - Next is: task definitaion -> Create new task definitision -> EC2 ->
     
     
     
     
![image](https://user-images.githubusercontent.com/44230257/141230023-2cc5c0da-247e-498e-8373-a2631f98da92.png)
![image](https://user-images.githubusercontent.com/44230257/141230069-3269f525-2e87-4e70-9dba-117d020e6f63.png)
![image](https://user-images.githubusercontent.com/44230257/141230080-48e008ff-963f-4f1e-90cc-395374678d4d.png)


