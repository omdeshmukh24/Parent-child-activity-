pipeline {

    agent any

    stages {

        stage('Test') {
            steps {
                sh '''
                pip3 install -r requirements.txt
                python3 -m pytest || true
                '''
            }
        }

        stage('Docker Build') {
            steps {
                sh '''
                docker build -t 172.31.45.245:5000/python-app:latest .
                '''
            }
        }

    }
}

