pipeline {
    agent {
        label 'Jenkins-Slave'
    }
    stages {
        // Define your pipeline stages here
        stage('SCM') {
            checkout scm
        }
        stage('SonarQube Analysis') {
            def scannerHome = tool 'sonarqube';
            withSonarQubeEnv() {
                sh "${scannerHome}/bin/sonar-scanner"
            }
        }
    }
}
