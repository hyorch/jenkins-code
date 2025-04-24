pipeline {
    agent any

    stages {
        stage('Prevare ENV') {
            steps {
                sh 'echo "Preparing environment..."'
            }
        }
      
        stage('SCM') {
            steps{
                checkout scm
            }
        }
        stage('SonarQube Analysis') {
            def scannerHome = tool 'Sonarqube-Tool';
            steps{
                withSonarQubeEnv() {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
       
       
        
    }
}
