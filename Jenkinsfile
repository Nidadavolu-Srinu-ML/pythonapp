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

        stage('generating report'){
            steps {
                withCredentials([string(credentialsId: 'report-token', variable: 'TOKEN')]) {
                script  {
                    sh '''
                       sudo docker exec -it sonarqube /bin/sh
                       cd /opt/sonarqube/extensions/plugins
                       mkdir reports
                       echo $TOKEN
                       java -jar sonar-cnes-report-4.2.0.jar -p sonarqubetest -t $TOKEN -o reports
                       ls -l
                       cd ../
                       rm -rf report
                    '''
                    }
                }
            }
        }
    }
}
