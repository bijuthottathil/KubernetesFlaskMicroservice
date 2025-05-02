# Create Python based Microservice to read weather from a city , deploy code in kubernetes
Part1) Deploying micro service to MiniKube
![image](https://github.com/user-attachments/assets/4b71deb4-3d2e-4e36-8e21-87f341ec8349)

Part 2) eploying micro service to EKS (AWS)
![image](https://github.com/user-attachments/assets/92c50437-46bc-4be9-9daa-c5b05d766532)


1. Setup virtual environment in Mac
python3 -m venv venvmicroservice
source venvmicroservice/bin/activate
KubernetesFlaskMicroservice % cd venvmicroservice
![image](https://github.com/user-attachments/assets/02b6741f-0a72-4455-8277-cccfdebb670e)

2. pip install flask
3. pip install requests
4. Write python code , requirement.txt, dockerfile, deployment.yaml,service.yaml

   ![image](https://github.com/user-attachments/assets/174a97af-a1af-4f7c-b298-4cfe27cb4c4c)

![image](https://github.com/user-attachments/assets/7c1cd3ce-54de-4b90-9433-08c19c20fd97)

![image](https://github.com/user-attachments/assets/6a43009d-a629-4571-8173-dd6d2f652f8c)

![image](https://github.com/user-attachments/assets/9824a283-8f54-4175-b72f-49a5288e07de)


5. Run file locally and test with postman

6. ![image](https://github.com/user-attachments/assets/13ad5f7a-0107-4188-a659-6f2dc67cbd1c)
7. Got expected result in postman

8. ![image](https://github.com/user-attachments/assets/87286900-0af2-4ee4-87ee-5df56e0e43b3)
9. if you are using mac, run below command to store docker image in minikube
10. eval $(minikube docker-env)
11. ![image](https://github.com/user-attachments/assets/56650453-1e88-4aa0-b4a7-1738bf3c43d3)
12. ![image](https://github.com/user-attachments/assets/ab0c8ce7-f7ec-4727-8234-156811b480be)
13. pods are running, we can verify it in MiniKube Dashboard
14. ![image](https://github.com/user-attachments/assets/ac5fd2b0-1b6e-4518-ad85-0cfeaec683ae)
15. ![image](https://github.com/user-attachments/assets/21993057-62bc-411b-9e51-7216f6aea832)
16. ![image](https://github.com/user-attachments/assets/3b3ae492-0f03-444e-a35a-415eeb2beefe)
17. Next step I am port fowarding 5000 to 8080 and validating service is running from pods
18. ![image](https://github.com/user-attachments/assets/c663efae-be73-4001-954e-0543f6136058)
19. Tested in postman, service is running fine
20. ![image](https://github.com/user-attachments/assets/2b0427e0-3ec4-4cec-a21b-132c1160dea4)


# See how this microservice can be deployed to EKS Cluster in AWS

I did few changes in Service.yaml and Deployment.yaml

You can see Load balancer is added and few port changes in service.yaml

in deployment.yaml, updated ECR url

![image](https://github.com/user-attachments/assets/1a346007-4a1c-42b2-8745-3666713f8e9d)

![image](https://github.com/user-attachments/assets/4658e25a-0c2f-4d44-83c7-2b79158a702b)

Step 1- Created EKS cluster from Aws CLI
 eksctl create cluster --name eks-cluster1 --version 1.31 --nodes=1 --node-type=t2.small --region us-east-1  

 ![image](https://github.com/user-attachments/assets/a6268f15-1fdb-42d0-97bc-55fd57d41af8)

Cluster is running ![image](https://github.com/user-attachments/assets/e6750c84-5c8e-435e-bb6f-b91e6a8d5af2)

I used below command to build image and push to ECR

1. docker buildx build --platform linux/amd64,linux/arm64  -t flaskapi .
2. docker tag flaskapi:latest 588268565787.dkr.ecr.us-east-1.amazonaws.com/flaskapi:latest
3. docker push 588268565787.dkr.ecr.us-east-1.amazonaws.com/flaskapi:latest
4.  aws eks --region us-east-1 update-kubeconfig --name eks-cluster1     -- to copy cluster config to my mac
5.  kubectl apply -f deployment.yaml
6.  ![image](https://github.com/user-attachments/assets/4b462559-6ab7-4c8a-92d9-44f8511f0912)
7.  kubectl apply -f service.yaml
8.  ![image](https://github.com/user-attachments/assets/9333351c-c4dc-4be6-a5bf-6c3562663aeb)
9.  ![image](https://github.com/user-attachments/assets/fc323384-4818-4b86-8894-392749a33167)

10.  From this , we can get API url -   ae28a2dfa5ef74b22907c2e5e096bf9f-1555352655.us-east-1.elb.amazonaws.com

11.  You can test this url in 2 ways  1) pasting url in browser 2) Via Postman
12.  Resutl in browser
13.  
14.  ![image](https://github.com/user-attachments/assets/60311268-f373-49b1-8ee0-b440366b7c04)

15.  Result by passing values in postman

16.  ![image](https://github.com/user-attachments/assets/4cab1ff0-8f72-40f6-9530-f55cdbb41974)


So service is working fine in EKS too :)








I have created ECR to store image and loaded image
![image](https://github.com/user-attachments/assets/19fdca2c-2759-40ce-90ee-b95e657d515f)




