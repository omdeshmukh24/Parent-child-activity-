pipeline {

    agent {
        label 'docker-agent'
    }

    environment {
        IMAGE = "omdeshmukh24/parent-child-app:v1"
        K8S_MASTER = "65.0.152.69"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/omdeshmukh24/Parent-child-activity-.git'
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'dockerhub',
                        usernameVariable: 'USER',
                        passwordVariable: 'PASS'
                    )
                ]) {

                    sh '''
                    echo "$PASS" | docker login \
                    -u "$USER" \
                    --password-stdin
                    '''
                }
            }
        }

        stage('Build Image') {
            steps {
                sh '''
                docker build -t $IMAGE .
                '''
            }
        }

        stage('Push Image') {
            steps {
                sh '''
                docker push $IMAGE
                '''
            }
        }

        stage('Deploy to Kubernetes') {
            steps {

                sshagent(credentials: ['k8s-master']) {

                    sh '''
                    scp -o StrictHostKeyChecking=no \
                    k8s/deployment.yaml \
                    jenkins@$K8S_MASTER:/home/jenkins/

                    ssh -o StrictHostKeyChecking=no \
                    jenkins@$K8S_MASTER << EOF

                    kubectl apply -f /home/jenkins/deployment.yaml

                    kubectl rollout status deployment/parent-child-app

                    kubectl get pods

                    EOF
                    '''
                }

            }
        }

    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }

        failure {
            echo 'Pipeline failed.'
        }
    }

}
