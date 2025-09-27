pipeline {
    agent any

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
              withCredentials([string(credentialsId: 'test-dockerhubpassword', variable: 'test-dockerhubpass')]) {
    // some block
                    script {
                        sh "docker login -u dvish2003 -p '${test-docker-hub-password}'"
                        echo "Logged in to Docker Hub as dvish2003"
                    }
                }
            }
        }

    }
}