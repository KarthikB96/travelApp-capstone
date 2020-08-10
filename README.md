Github link: https://github.com/KarthikB96/travelApp-capstone
This Capstone project is based on a travel blog where users enter photos,caption and description in their post. For each rubric a screenshot has been attached .

The main blocks in the project is backend-feed,backend-user,frontend and reverseproxy. each block is containerised and deployed in eks.

Dockerhub repositories links:
https://hub.docker.com/repository/docker/karthikb96/travelapp-api-user
https://hub.docker.com/repository/docker/karthikb96/travelapp-api-feed
https://hub.docker.com/repository/docker/karthikb96/travelapp-reverseproxy
https://hub.docker.com/repository/docker/karthikb96/travelapp-frontend

#Description:
1. The Project is based on a travel blogging website where travellers can share images and their story and details.
2. The Deployment folder is responsible for the building the reverseproxy for the backend as well as the deployment of the application to Kubernetes.
3. The Backend is divided into two parts one for feed functionalities (post and image upload)and another for user functionalities (registration and authentication). Frontend is in ionic.

Setup:
Create Docker Images:
1.Reverse Proxy Image
Navigate to the travelApp-capstone\deployment\Docker directory.
Build a docker image of the reverseproxy with docker build -t {your_docker_hub_username}/travelapp-reverseproxy .
2.Backend User Image
Navigate to the travelApp-capstone\travelapp-api-feed directory.
Build a docker image of the backend user microservice with docker build -t {your_docker_hub_username}/travelapp-api-feed .
3.Backend Feed Image
Navigate to the travelApp-capstone\travelapp-api-user directory.
Build a docker image of the backend feed microservice with docker build -t {your_docker_hub_username}/travelapp-api-user.
4.Frontend Image
Navigate to the travelapp-frontend/ directory.
Build a docker image of the frontend with docker build -t {your_docker_hub_username}/travelapp-frontend .

Publish Images to Docker Hub
Publish the reverseproxy image with docker push {your_docker_hub_username}/travelapp-reverseproxy.
Publish the backend user image with docker push {your_docker_hub_username}/travelapp-api-user.
Publish the backend feed image with docker push {your_docker_hub_username}/travelapp-api-feed.
Publish the frontend image with docker push {your_docker_hub_username}/travelapp-frontend.

Deploy to Kubernetes Cluster
Navigate to the travelApp-capstone\deployment\k8s\ directory.
configuration values are entered in aws-secret.yaml, env-configmap.yaml, env-secret.yaml.
docker hub images are entered in backend-feed-deployment.yaml, backend-user-deployment.yaml, frontend-deployment.yaml, reverseproxy-deployment.yaml files.
Deploy to Kubernetes cluster with kubectl apply -f {file_name_deployment}.yaml and kubectl apply -f {file_name_service}.yaml or each block.

Start App As Container On Local System
Navigate to the travelApp-capstone\deployment\Docker directory.
Boot up images with docker-compose up.


