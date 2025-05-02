# Create Python based Microservice to read weather from a city , deploy code in kubernetes


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







