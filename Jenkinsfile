pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials-id') // Replace with your Jenkins credentials ID
        DCOKER_IMAGE = 'your-dockerhub-username/your-image-name' // Replace with your Docker Hub username and image name}

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning repository...'
                // Add your clone steps here
                git branch: 'main', url: 'https://github.com/dvish2003/DOCKER-AUTOMATE-PIPELINE.git'

            }
        }

          stage('Login to Docker Hub') {
            steps {
                withCredentials([string(credentialsId: 'test-dockerhub-password', variable: 'test-docker-hub-password')]) {
                    script {
                        sh "docker login -u dvish2003 -p '${test-docker-hub-password}'"
                        echo "Logged in to Docker Hub as dvish2003"
                    }
                }
            }
        }

       
}