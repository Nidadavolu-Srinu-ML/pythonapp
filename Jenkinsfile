pipeline {
    agent {
        label 'Jenkins-Slave'
    }
    stages {
        // Define your pipeline stages here
        stage('SCM') {
            steps {
               checkout scm
            }
        }
        stage('SonarQube Analysis') {
            steps {
                scrpt  {
                    def scannerHome = tool 'sonarqube';
                    withSonarQubeEnv() {
                    sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
    }
}
