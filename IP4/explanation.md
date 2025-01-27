# YOLO Project

## 1. Choice of Base Image
The project uses the following base images to build the containers for client, backend, and MongoDB:

- **Client Image**: `node:16-alpine3.16`
- **Backend Image**: `node:16-alpine3.16`
- **MongoDB Image**: `mongo:6.0`

These base images are chosen for their compact and efficient nature, ideal for running Node.js and MongoDB applications.

## 2. Dockerfile Directives Used in the Creation and Running of Each Container

Two Dockerfiles are used, one for the **client** and one for the **backend**. These Dockerfiles set up the necessary environment, install dependencies, copy the application code, and define how each service should run in the container. The client Dockerfile handles the building and serving of the frontend application, while the backend Dockerfile handles the backend Node.js service.

## 3. Docker Compose Networking

The `docker-compose.yml` defines the following service configurations:

- **Client**: Exposes port 3000.
- **Backend**: Exposes port 5000.
- **MongoDB**: Exposes port 27017.

These services are connected through a custom bridge network, `yolo-network`, ensuring they can communicate with each other during development.

## 4. Docker Compose Volume Definition and Usage

A persistent volume `mongodata` is defined for MongoDB to ensure that data is retained even if the MongoDB container is stopped or removed. This volume is crucial for ensuring the database data persists between container restarts.

## 5. Git Workflow to Achieve the Task

- Fork and clone the repository to your local machine.
- Create Dockerfiles for both the frontend and backend services, and a `docker-compose.yml` file to manage the containers.
- Build and push the Docker images to your preferred registry.
- Deploy the application using Kubernetes, with appropriate configurations for backend and frontend deployments.

## 6. Kubernetes Deployment

The backend and frontend services are deployed on Kubernetes using the following general approach:

1. **Create Kubernetes manifests** for deployment and service definitions for both frontend and backend.
2. **Apply the Kubernetes manifests** using `kubectl apply -f <manifest-file>.yaml`.
3. **Expose the services** using a Kubernetes `LoadBalancer` service or `NodePort` for external traffic access.

## 7. Accessing the Application

After deploying the application, the frontend can be accessed via the external IP address provided by the Kubernetes `LoadBalancer` service. You can retrieve this IP using the following command:

```bash
kubectl get svc
You can access the application in your browser by navigating to:
http://35.192.168.243

