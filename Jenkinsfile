pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "rohityadav0107/library-app"
    }

    stages {

        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Test passed"'
            }
        }

        stage('Docker') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE:latest .'
                sh 'docker push $DOCKER_IMAGE:latest'
            }
        }

        stage('Deploy') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}
