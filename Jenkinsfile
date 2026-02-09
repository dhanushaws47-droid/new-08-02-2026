pipeline {
    agent any

    environment {
        IMAGE = "dhanushdock1/mysite:${BUILD_NUMBER}"
    }

    stages {

        stage('Build') {
            steps {
                echo 'Building app...'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t $IMAGE .'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $IMAGE'
            }
        }
    }
}
