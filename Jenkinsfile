pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/nguyenhuylam/docker-spring-boot-java-web-service-example'
            }
        }

        stage('Build Application') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Verify JAR') {
            steps {
                sh 'ls -lh target/'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t lamnguyen1999/spring-boot-app:v1 .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker login -u lamnguyen1999 -p huylam110599'
                sh 'docker push lamnguyen1999/spring-boot-app:v1'
            }
        }
    }
}
