pipeline {
    agent any

    stages {
        stage("Build Docker Image") {
            steps {
                script {
                    dockerapp = docker.build("tiagommota/kube-news:${env.BUILD_ID}" , "--file ./src/dockerfile ./src")
                }
            }
        
    

    stages {
        stage("Push Docker Image") {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
                        dockerapp.push('latest')
                        dockerapp.push("${env.BUILD_ID}")
                }
            }
        }
    }
}
}
}