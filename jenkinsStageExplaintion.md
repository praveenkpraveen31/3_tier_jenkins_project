# Jenkinsfile Explanation

## Overview
This Jenkinsfile defines a **CI/CD pipeline** for building, tagging, pushing, and deploying a **3-tier application** using Docker and Kubernetes. Below is a breakdown of each section and its functionality.

## Jenkinsfile Code Breakdown

### 1. Pipeline Definition
```groovy
pipeline {
    agent any
```
- `pipeline {}`: Defines a declarative Jenkins pipeline.
- `agent any`: Runs the pipeline on any available Jenkins agent.

### 2. Environment Variables
```groovy
    environment {
        DOCKER_USERNAME = "praveeen267"
        IMAGE_TAG = "${env.BUILD_NUMBER}"
    }
```
- `DOCKER_USERNAME`: Stores the DockerHub username.
- `IMAGE_TAG`: Uses the Jenkins build number as the image tag.

### 3. Stages
#### **Build Backend**
```groovy
        stage('Build Backend') {
            steps {
                dir('backend') {
                    sh "docker build -t ${DOCKER_USERNAME}/three-tier-backend:${IMAGE_TAG} ."
                    sh "docker tag ${DOCKER_USERNAME}/three-tier-backend:${IMAGE_TAG} ${DOCKER_USERNAME}/three-tier-backend:latest"
                }
            }
        }
```
- `stage('Build Backend')`: Defines the backend build stage.
- `dir('backend')`: Moves into the `backend/` directory.
- `docker build`: Builds the Docker image.
- `docker tag`: Tags the image with `latest`.

#### **Build Frontend**
```groovy
        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    sh "docker build -t ${DOCKER_USERNAME}/three-tier-frontend:${IMAGE_TAG} ."
                    sh "docker tag ${DOCKER_USERNAME}/three-tier-frontend:${IMAGE_TAG} ${DOCKER_USERNAME}/three-tier-frontend:latest"
                }
            }
        }
```
- Similar to the backend, this stage builds the frontend Docker image.

#### **Push to DockerHub**
```groovy
        stage('Push to DockerHub') {
            steps {
                sh "docker push ${DOCKER_USERNAME}/three-tier-backend:${IMAGE_TAG}"
                sh "docker push ${DOCKER_USERNAME}/three-tier-backend:latest"
                sh "docker push ${DOCKER_USERNAME}/three-tier-frontend:${IMAGE_TAG}"
                sh "docker push ${DOCKER_USERNAME}/three-tier-frontend:latest"
            }
        }
```
- Pushes the backend and frontend images to DockerHub.

#### **Deploy to Kubernetes**
```groovy
        stage('Deploy to Kubernetes') {
            steps {
                sh "kubectl apply -f k8s-manifests/"
            }
        }
```
- `kubectl apply -f k8s-manifests/`: Deploys the updated images to Kubernetes.

### 4. Post Actions
```groovy
    post {
        always {
            sh "echo 'Pipeline execution completed'"
        }
    }
```
- `always`: Executes the command regardless of success or failure.
- `echo`: Prints a message indicating pipeline completion.

## Summary of Pipeline Stages
1. **Build Backend**: Builds and tags the backend Docker image.
2. **Build Frontend**: Builds and tags the frontend Docker image.
3. **Push to DockerHub**: Pushes both images to DockerHub.
4. **Deploy to Kubernetes**: Deploys the application using Kubernetes manifests.
5. **Post Actions**: Prints a message after pipeline execution.

This Jenkinsfile automates the CI/CD process, ensuring continuous integration and deployment of the 3-tier application.

