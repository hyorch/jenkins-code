pipeline {
    agent any

    stages {
        stage('Prevare ENV') {
            steps {
                sh 'echo "Preparing environment..."'
            }
        }
        stage('Show Version') {
            steps {
                sh 'ls -la'
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Building..."'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Testing..."'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Deploying..."'
            }
        }
        stage('Cleanup') {
            steps {
                sh 'echo "Cleaning up..."'
            }
        }
        stage('Post Actions') {
            steps {
                sh 'echo "Performing post actions..."'
            }
        }
        stage('Notify') {
            steps {
                sh 'echo "Notifying..."'
            }
        }
    }
}
