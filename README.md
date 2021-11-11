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




![image](https://user-images.githubusercontent.com/44230257/141246372-2b12ff79-cbec-47d2-a78a-ab3ac816b762.png)
![image](https://user-images.githubusercontent.com/44230257/141246387-6d34ec9f-de49-40ae-94c4-098d4a6fa14f.png)
![image](https://user-images.githubusercontent.com/44230257/141246399-a3f375f5-524b-4b68-990e-38ceedbf402e.png)
![image](https://user-images.githubusercontent.com/44230257/141246408-381e7619-8125-4243-8eba-d9c5ef3b50e8.png)
![image](https://user-images.githubusercontent.com/44230257/141246445-de63f9b2-00a5-49f2-b6ee-fb476e95ac27.png)
![image](https://user-images.githubusercontent.com/44230257/141246484-feb3b93b-6ce9-448b-8bba-d57150e6e28b.png)
![image](https://user-images.githubusercontent.com/44230257/141246498-8e905d3c-63c2-498f-bca0-97c5be7e1aec.png)
![image](https://user-images.githubusercontent.com/44230257/141246518-ff36f923-92d6-4e90-a8f0-f3a98ee35ecb.png)
![image](https://user-images.githubusercontent.com/44230257/141246541-6b39c1d4-cceb-4dce-a9f1-4332ed51225f.png)
![image](https://user-images.githubusercontent.com/44230257/141246596-2ec5c356-bbb0-4f59-b60b-caa85cada072.png)
![image](https://user-images.githubusercontent.com/44230257/141246614-56e81b6a-209f-4b03-8100-14e71136b073.png)
![image](https://user-images.githubusercontent.com/44230257/141246622-0af008fc-00f8-4f8f-bd55-687789aa3898.png)
![image](https://user-images.githubusercontent.com/44230257/141246631-7300d6db-addd-4461-a02d-00570df4316b.png)
![image](https://user-images.githubusercontent.com/44230257/141246643-b3235e3b-459a-46a1-945c-bfc51a920de0.png)
![image](https://user-images.githubusercontent.com/44230257/141246651-51fe11d4-5f3b-4823-ae1e-c8500b4f9302.png)
![image](https://user-images.githubusercontent.com/44230257/141246713-b917cb0d-273b-48f9-aecb-b9026bd165f1.png)
![image](https://user-images.githubusercontent.com/44230257/141246720-73af6c2a-cc16-449f-b07e-4e8cee38567f.png)
![image](https://user-images.githubusercontent.com/44230257/141246731-244783f1-a8f4-4980-844d-61c2a61ae676.png)
![image](https://user-images.githubusercontent.com/44230257/141246745-c3402656-5f72-4d74-b0d5-94428f4d0b3c.png)
![image](https://user-images.githubusercontent.com/44230257/141246752-52512778-54bb-4cd8-98df-aa8ddcea17ba.png)
![image](https://user-images.githubusercontent.com/44230257/141246770-073e0871-b846-4a2d-b875-1df80874b100.png)
![image](https://user-images.githubusercontent.com/44230257/141246787-a384bc07-175b-42e4-bfae-4d506e3bb9ae.png)
![image](https://user-images.githubusercontent.com/44230257/141246813-4149f4a8-ca6d-4f13-9f99-7f6c2dee1d30.png)
![image](https://user-images.githubusercontent.com/44230257/141246830-385c4490-d83a-417f-a239-476a561d0d08.png)
![image](https://user-images.githubusercontent.com/44230257/141246851-c1bf1275-f22b-4f56-9e36-cc2aa9860003.png)
![image](https://user-images.githubusercontent.com/44230257/141246865-6658c5ff-9d1a-4986-8cdd-e6d76c4ada74.png)
![image](https://user-images.githubusercontent.com/44230257/141246880-bf4fb7e9-040b-4453-b9c9-65f4dbbd28c9.png)
![image](https://user-images.githubusercontent.com/44230257/141246889-9de7c082-06e2-4225-a952-d54357a69574.png)
![image](https://user-images.githubusercontent.com/44230257/141246904-fa2de717-09de-4158-b44b-d5f3dcd2d1e4.png)
![image](https://user-images.githubusercontent.com/44230257/141246920-701f0bb7-4cce-460c-860e-55f3a72f2996.png)
![image](https://user-images.githubusercontent.com/44230257/141246930-f260f058-713c-48b4-952e-5306094ddc93.png)
![image](https://user-images.githubusercontent.com/44230257/141246941-68d86f64-7e46-4e1d-98b0-e8858c46f30d.png)
![image](https://user-images.githubusercontent.com/44230257/141246953-2f0db6c5-c046-48d7-bc15-6cb633e9a417.png)
























