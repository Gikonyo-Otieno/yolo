1. Choice of Base Image
The base image used to build the containers is node:16-alpine3.16, derived from the Alpine Linux distribution, making it lightweight and compact.

Base Images Used:

Client: node:16-alpine3.16
Backend: node:16-alpine3.16
MongoDB: mongo:6.0

2. Dockerfile Directives Used in the Creation and Running of Each Container
Two Dockerfiles were created: one for the Client and the other for the Backend.

3. Docker Compose Networking
The docker-compose.yml file defines the networking configuration for the project. Application ports are allocated, and a custom bridge network is created for communication between services.

4. Docker Compose Volume Definition and Usage
The Docker Compose file includes volume definitions to persist MongoDB data. This ensures that the database data is retained even if the container is stopped or removed.

5 Git Workflow to achieve task
-Fork the repository from the original repository.

-Clone the repo: git@github.com:Maubinyaachi/yolo-Microservice.git

-Create a .gitignore file to exclude unnecessary files and directories from version control.

-Added Dockerfile for the client to the repo: git add client/Dockerfile

-Add Dockerfile for the backend to the repo: git add backend/dockerfile

-Committed the changes: git commit -m "Added Dockerfiles"

-Added docker-compose file to the repo: git add docker-compose.yml

-Committed the changes: git commit -m "Added docker-compose file"

-Pushed the files to github: git push 

-Built the client and backend images: docker compose build

-Pushed the built imags to docker registry: docker compose push

-Deployed the containers using docker compose: docker compose up

6. Debugging Measures Applied
Node Version Issue:
If the application failed to run due to a Node version compatibility issue. Instead of downgrading Node, the following command should be used to bypass the problem:

    export NODE_OPTIONS=--openssl-legacy-provider
    npm start

Port Conflicts:
Verified that ports 3000, 5000, and 27017 were not in use before running the containers.

7. Best Practices Followed
-Lightweight Images: Used node:16-alpine3.16 for optimized performance and smaller image sizes.
-Environment Variables: Utilized ENV directives in Dockerfiles to configure applications for production environments.
-Data Persistence: Leveraged Docker volumes for MongoDB data storage.

8. Deployed Images on DockerHub
The Docker images were pushed to DockerHub with proper version tags:

Client Image: gikonyo14/gikonyo-yolo-client
Backend Image: gikonyo14/gikonyo-yolo-backend