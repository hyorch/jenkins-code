pipeline {
    agent any

    stages {
        stage('Prevare ENV') {
            steps {
                sh 'echo "Preparing environment..."'
            }
        }
      
        stage('SCM') {
            checkout scm
        }
        stage('SonarQube Analysis') {
            def scannerHome = tool 'Sonarqube-Tool';
            withSonarQubeEnv() {
                sh "${scannerHome}/bin/sonar-scanner"
            }
        }
       
       
        
    }
}
