pipeline {
    agent any

    stages {
        stage("Build Docker Image") {
            steps {
                script {
                    dockerapp = docker.build("tiagommota/kube-news:${env.BUILD_ID}" , "--file ./src/dockerfile ./src")
                }
            }
        }
    }
}