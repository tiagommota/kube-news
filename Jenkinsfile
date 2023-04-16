pipeline {
    agent any

    stages {
        stage("Build Docker Image") {
            steps {
                script {
                    dockerapp = docker.build("tiagommota/kube-news:${env.BUILD_ID}" , "-f ./src/dockerfile ./src")
                }
            }
        }

        stage("Push Docker Image") {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub'){
                        dockerapp.push('latest')
                        dockerapp.push("${env.BUILD_ID}")
                    }
                    
                }
            }
        }

        stage("Deploy Kubernets"){

            steps {

                withkubeConfig ([credentialsid: 'kube_config']) {
                    sh 'kubectl apply -f ./k8s/deployment.yaml'                 
                }

            }

        }
    }
}
