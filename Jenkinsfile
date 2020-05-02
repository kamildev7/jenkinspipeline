pipeline {
    agent any

    tools {
        maven 'maven3.5.2'
    }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                build job: 'deploy-to-staging'
            }
        }
    }
}