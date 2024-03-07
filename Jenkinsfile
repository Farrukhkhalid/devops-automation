pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Build the Docker image
                    sh 'docker build -t farrukhkhalid/jenkinstest .'
                }
            }
        }
        stage('Push') {
            steps {
                script {
                    // Log in to Docker Hub
                    withCredentials([usernamePassword(credentialsId: 'Git_cred', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh 'sudo docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                    }
                    
                    // Push the Docker image to Docker Hub
                    sh 'sudo docker push farrukhkhalid/jenkinstest'
                }
            }
        }
    }
}