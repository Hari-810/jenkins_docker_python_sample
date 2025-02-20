pipeline {
    agent any

    environment {
        IMAGE_NAME = 'flask-app'
        CONTAINER_NAME = 'flask_container'
        PORT = '5000'        
        GIT_REPO = 'https://github.com/Hari-810/jenkins_docker_python_sample.git'
        GIT_BRANCH = 'main' // Change this to the correct branch
    
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Hari-810/jenkins_docker_python_sample.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t $IMAGE_NAME ."
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh "docker stop $CONTAINER_NAME || true"
                    sh "docker rm $CONTAINER_NAME || true"
                    sh "docker run -d --name $CONTAINER_NAME -p $PORT:$PORT $IMAGE_NAME"
                }
            }
        }
    }
}
