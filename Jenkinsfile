pipeline{
    agent any

    stages{
        stage('Checkout SCM'){
            steps{
                checkout scm
            }
        }
        stage('Build FrontEnd'){
            agent {
                docker { image 'node:current-alpine3.13'}
                
            }
            steps{
                sh 'npm install'
                sh 'npm build'
            }

        }
        stage('Build BackEnd'){
            agent{
                    docker {image 'docker pull maven:3.6-adoptopenjdk-8'}
                }
            steps{
                sh 'mvn package'
                archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
            }
            
        }

    }
}