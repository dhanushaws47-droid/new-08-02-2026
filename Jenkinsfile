pipeline {
agent any

```
environment {
    IMAGE = "dhanushdock1/mysite:${BUILD_NUMBER}"
}

stages {

    stage('Build Docker Image') {
        steps {
            sh 'docker build -t $IMAGE .'
        }
    }

    stage('Push to DockerHub') {
        steps {
            sh 'docker push $IMAGE'
        }
    }

    stage('Deploy to EC2') {
        steps {
            sh """
            ssh -o StrictHostKeyChecking=no -i ~/key.pem ec2-user@13.61.0.189 '
                docker pull $IMAGE
                docker stop mysite || true
                docker rm mysite || true
                docker run -d --name mysite -p 80:80 $IMAGE
            '
            """
        }
    }
}
```

}
