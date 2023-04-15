pipeline {
    agent any

    stages{

        stage ("Build Docker Image")
            steps {
                scrips {
                    dockeraoo = docker.bulild("tiagommota/kube-news:${env.BUILD_ID}", '-f ./src/dockerfile ./src')

                }
            }

    }


}