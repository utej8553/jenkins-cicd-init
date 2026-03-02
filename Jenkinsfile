pipeline {
    agent { label 'agent-1' }

    environment {
        IMAGE_NAME = "myapp"
        CONTAINER_NAME = "myapp-container"
    }

    stages {

        stage('Clone') {
            steps {
                deleteDir()
                git branch: 'main', url: 'https://github.com/utej8553/demo-simple-server'
            }
        }

        stage('Build Jar') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t utej8553/$IMAGE_NAME .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker push utej8553/$IMAGE_NAME'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop $CONTAINER_NAME || true
                docker rm $CONTAINER_NAME || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker run -d -p 9000:9000 --name $CONTAINER_NAME utej8553/$IMAGE_NAME
                '''
            }
        }
    }
}
