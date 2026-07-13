pipeline{
    agent any
    environment{
        PATH = "/opt/maven/bin:${PATH}"
        scannerHome = tool 'sonarqubeScanner'
    }
    stages{
        stage('Maven build'){
            steps{
                sh 'mvn clean package'
            }
        }

        stage('print sonar directory'){
            steps{
                echo "Following is directory for sonarScanner ${scannerHome}"
            }
        }

        stage('SonarQube Analysis'){
            steps{
                withSonarQubeEnv('sonarqubeServer'){
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
        
    }
}

