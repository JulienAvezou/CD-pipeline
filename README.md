# CD-pipeline
Notes from DevSecOps ch.6 Build a CD Pipeline

We will deploy our application and learn security concepts along the way

1. Create ECR on AWS
  - configure aws ecr credentials
  - aws-cli added in our job

<img width="1018" alt="Capture d’écran 2024-06-01 à 11 22 13" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/53859b17-535b-4135-af0b-eed01e060e35">

2. Build and push image to ECR
<img width="1030" alt="Capture d’écran 2024-06-01 à 22 18 45" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/4d5014bc-1d82-4d4e-8722-429ad8876584">
<img width="606" alt="Capture d’écran 2024-06-01 à 21 20 08" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/92e1955c-17c0-4926-a6dc-01fc2b3d58b7">
<img width="1024" alt="Capture d’écran 2024-06-01 à 21 19 59" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/7dbd199f-0333-4b93-aa24-e35bf2bdec2a">

3. Create EC2 instance
<img width="1103" alt="Capture d’écran 2024-06-04 à 19 47 06" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/a14cbfd7-fb68-4e64-8f92-f36622fe60e8">

5. Install docker on EC2 instance
<img width="436" alt="Capture d’écran 2024-06-04 à 19 58 03" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/8d7431aa-4fe1-4249-aced-67a7c4032ee0">

7. Configure AWS CLI to connect to ECR repository
<img width="486" alt="Capture d’écran 2024-06-04 à 20 08 33" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/9bda12bc-fc40-4757-b69a-10c9371b8e7d">

8. Configure SSH client and add as job to pipeline to deploy the image
<img width="961" alt="Capture d’écran 2024-06-04 à 21 37 22" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/e93e31df-66f4-43e3-b7d6-9ede49a49238">
<img width="771" alt="Capture d’écran 2024-06-04 à 21 58 40" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/527bb54b-93e4-4727-baa4-6ad49ab0d543">

---

Gitlab shared runners:
available to all the projects for every gitlab user
-> no insight or control over shared runners
= best practice is to use self-managed gitlab runners
give that runner an AWS role

7. Create EC2 instance
<img width="1146" alt="Capture d’écran 2024-06-04 à 22 52 11" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/85942537-af0c-4054-a9ed-bc3e6f309e49">

9. Create gitlab runner
<img width="544" alt="Capture d’écran 2024-06-04 à 22 14 34" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/151858a3-42ef-4032-a833-6f72a1c48ea0">

10. Install gitlab runner
<img width="387" alt="Capture d’écran 2024-06-04 à 22 17 51" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/33cc751d-bb41-4d2f-9607-fe6129240460">

11. Register gitlab runner
<img width="459" alt="Capture d’écran 2024-06-04 à 22 21 16" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/484fd935-4f07-4ed0-ae20-9e3f61289144">

12. Optimize caching image layers thanks to self-managed runner executed in shell of our server
<img width="1019" alt="Capture d’écran 2024-06-04 à 22 32 16" src="https://github.com/JulienAvezou/CD-pipeline/assets/62488871/09a99c82-71e8-48fb-ae89-1eab4c58024a">

Troubleshooting runner:
df -h (check remaining space)
docker image prune (remove dangling images to free up some space)
gitlab-runner start
gitlab-runner status
gitlab-runner run
