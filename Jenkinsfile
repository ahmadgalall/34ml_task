pipeline {
    agent any

    stages {
        stage('Build Test Image') {
            steps {
                git branch: 'main', url: 'https://github.com/ahmadgalall/34ml_task.git'
                script {
                    docker.build("test_image", "--file Dockerfile .")
                }
            }
        }

        stage('Test Application') {
            steps {
                script {
                    docker.run("test_image")
                }
            }
        }

        stage('Build Release Image and Push to Docker Hub') {
            environment {
                DOCKERHUB_REGISTRY = "docker.io"
                DOCKERHUB_USERNAME = credentials("<username>")
                DOCKERHUB_PASSWORD = credentials("<pass>")
                DOCKERHUB_REPO = "https://hub.docker.com/repository/docker/ahmadgalal/34ml_task/"
            }
            steps {
                git branch: 'main', url: 'https://github.com/ahmadgalall/34ml_task.git'
                script {
                    docker.build("release_image", "--file Dockerfile-build .")
                    docker.withRegistry("${DOCKERHUB_REGISTRY}", "${DOCKERHUB_USERNAME}", "${DOCKERHUB_PASSWORD}") {
                        docker.image("release_image").push("${DOCKERHUB_REPO}")
                    }
                }
            }
        }
    }
}