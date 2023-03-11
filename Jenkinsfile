pipeline {
    agent any
    stages {
        stage('Clone stage') {
            steps {
                git credentialsId: 'hook', url: 'https://gitlab.com/kma2023/webhook.git'
            }
        }
        stage('Push registry') {
            steps {
                withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/') {
                    sh label: '', script: 'docker build -t manhkma/jenkins-test-nodejs:v10 .'
                    sh label: '', script: 'docker push manhkma/jenkins-test-nodejs:v10'
                }
            }
        }
    }
}
