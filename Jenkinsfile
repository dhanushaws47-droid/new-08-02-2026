pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t mysite .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8080:80 mysite || true'
            }
        }
    }
}
