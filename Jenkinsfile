pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t dhanushdock1/mysite:${BUILD_NUMBER} .'
            }
        }

        stage('Push to DockerHub') {
            steps {
                sh 'docker push dhanushdock1/mysite:${BUILD_NUMBER}'
            }
        }

        stage('Deploy to EC2') {
            steps {
                sh """
                ssh -o StrictHostKeyChecking=no -i /tmp/ec2-key.pem ec2-user@YOUR_PUBLIC_IP '
                    docker pull dhanushdock1/mysite:${BUILD_NUMBER}
                    docker stop mysite || true
                    docker rm mysite || true
                    docker run -d --name mysite -p 80:80 dhanushdock1/mysite:${BUILD_NUMBER}
                '
                """
            }
        }

<<<<<<< HEAD
        stage('Run Container') {
            steps {
                sh 'docker run -d --name $CONTAINER -p 8082:80 $IMAGE'
            }
        }
=======
>>>>>>> 49292fc (added auto EC2 deploy)
    }
}
