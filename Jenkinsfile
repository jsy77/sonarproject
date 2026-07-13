pipeline {
    agent any
    environment{
        PATH="/opt/maven/bin:${PATH}"
    }
    stages{
        stage('build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('sonar qube analysis'){
            environment{
                scannerHome = tool 'sonarqubeScanner'
            }
            steps{
                withSonarQubeEnv('sonarqubeServer'){
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
        stage('lets check sonnarhome path'){
            environment{
                scannerHome = tool 'sonarqubeScanner'
            }
            steps{
                echo "scanner path is : ${scannerHome}"
            }
            
        }
    }
}
