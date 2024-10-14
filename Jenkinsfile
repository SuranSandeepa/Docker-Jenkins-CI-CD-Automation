pipeline {
    agent any  // Runs the pipeline on any available agent
    
    stages { 
        stage('SCM Checkout') {  // Stage to check out the source code from GitHub
            steps {
                retry(3) {  // Retries the git checkout up to 3 times if it fails
                    git branch: 'main', url: 'https://github.com/SuranSandeepa/Docker-Jenkins-CI-CD-Automation.git'  // Clones the 'main' branch from the given repository
                }
            }
        }
        stage('Build Docker Image') {  // Stage to build the Docker image
            steps {  
                bat 'docker build -t suransandeepa/nodeapp-cicd:%BUILD_NUMBER% .'  // Builds a Docker image with a tag using the Jenkins build number
            }
        }
        stage('Login to Docker Hub') {  // Stage to log in to Docker Hub
            steps {
                // Retrieves Docker Hub credentials stored in Jenkins
                withCredentials([string(credentialsId: 'zero-dockerhub-pass', variable: 'zero-dockerhubpass')]) {
                    script {
                        // Logs in to Docker Hub using the username and the credentials passed as an environment variable
                        bat "docker login -u suransandeepa -p %zero-dockerhubpass%"
                    }
                }
            }
        }
        stage('Push Image') {  // Stage to push the Docker image to Docker Hub
            steps {
                bat 'docker push suransandeepa/nodeapp-cicd:%BUILD_NUMBER%'  // Pushes the Docker image with the current Jenkins build number to Docker Hub
            }
        }
    }
    post {
        always {  // Actions to always run after the pipeline finishes, regardless of success or failure
            bat 'docker logout'  // Logs out from Docker Hub to ensure the credentials are cleared
        }
    }
}
