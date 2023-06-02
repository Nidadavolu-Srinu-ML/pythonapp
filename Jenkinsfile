pipeline {
    agent {
        label 'Jenkins-Slave'
    }
    stages {
        // Define your pipeline stages here
        stage('SonarQube Analysis') {
            steps {
                script  {
                    def scannerHome = tool 'sonarqube';
                    withSonarQubeEnv() {
                    sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
        
        stage('Generating Sonarqube report') {
           steps {
                build job: 'generate-sonarqube-report'
            }
        }
    }
}
