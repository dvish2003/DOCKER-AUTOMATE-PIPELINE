pipeline {
    agent any
    
    stages {
        stage('SCM Checkout') {
            steps {
                retry(3) {
                git branch: 'main', url: 'https://github.com/dvish2003/DOCKER-AUTOMATE-PIPELINE.git'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t dvish2003/nodeapp-cuban:${BUILD_NUMBER} .'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                  withCredentials([string(credentialsId: 'dockerhubpassword', variable: 'dockerhub-pass')]) {
                    script {  
                        sh "docker login -u dvish2003 -p '${dockerhub-pass}'"
                    }
                }
            }
        }
        stage('Push Image') {
            steps {
                sh "docker push dvish2003/nodeapp-cuban:${BUILD_NUMBER}"
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}