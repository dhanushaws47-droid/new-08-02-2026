pipeline {
    agent any

    environment {
        IMAGE = "dhanushdock1/mysite:${BUILD_NUMBER}"
        CONTAINER = "mysite"
    }

    stages {

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

        stage('Cleanup Old Container') {
            steps {
                sh 'docker stop $CONTAINER || true'
                sh 'docker rm $CONTAINER || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d --name $CONTAINER -p 8080:80 $IMAGE'
            }
        }
    }
}
