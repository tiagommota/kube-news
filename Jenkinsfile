pipeline {
    agent any

    stages{

        stage ("Build Docker Image")
            steps {
                scrips {
                    dockerapp = docker.bulild("tiagommota/kube-news:${env.BUILD_ID}", '-f ./src/dockerfile ./src')

                }
            }

    }


}