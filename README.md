# CI/CD Pipeline for Node.js Application

## Description
This repository contains a complete CI/CD pipeline setup for a Node.js application using **Jenkins** and **Docker**. The project features an **Express.js** server with multiple routes and integrates automated testing, Docker containerization, and deployment processes.

## Project Structure
- **`index.js`**: 
  The main server file that initializes an Express.js application with three routes:

- **`test.js`**: 
  Contains unit tests for the Express routes using the **Supertest** library to ensure that the application responds correctly to HTTP requests.

- **`Dockerfile`**: 
  A configuration file to build a Docker image for the application. It sets up the environment, installs dependencies, exposes the application port, and defines the command to start the app.

- **`Jenkinsfile`**: 
  A pipeline script for Jenkins that automates the following stages:
  - **SCM Checkout**: Retrieves the source code from the GitHub repository.
  - **Build Docker Image**: Builds a Docker image of the application using the Dockerfile.
  - **Login to Docker Hub**: Logs into Docker Hub using stored credentials in Jenkins.
  - **Push Image**: Pushes the built Docker image to Docker Hub with a unique tag based on the Jenkins build number.

## Getting Started
1. **Clone the repository**:
   ```bash
   git clone https://github.com/SuranSandeepa/Docker-Jenkins-CI-CD-Automation.git
