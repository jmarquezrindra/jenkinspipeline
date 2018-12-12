pipeline {
    agent any
    stages{
        stage('Build'){
            steps{
                bat '"D:/ENDESA DISTRIBUCION/00_Formacion/00_Integracion_Continua/apache-maven-3.6.0/bin"/mvn.cmd clean package'
            }
            post{
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to staging'){
            steps{
                build job: 'deploy-to-staging'
            }
        }
    }
}
