pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "lamnguyen1999/spring-boot-app:v1"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/jaiswaladi246/docker-spring-boot-java-web-service-example.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $DOCKER_IMAGE .'
                }
            }
        }

        stage('Login to Docker Hub') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'bfde624c-5d6b-4cf7-af1e-06f32eda305d', usernameVariable: 'lamnguyen1999', passwordVariable: 'huylam110599')]) {
                        sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    }
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }

        stage('Cleanup') {
            steps {
                sh 'docker rmi $DOCKER_IMAGE'
            }
        }
    }
}
