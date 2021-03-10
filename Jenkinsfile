pipeline{
    agent {
        label 'node1'
    }
    tools {
       jdk 'jdk8'
       maven 'maven3'
    }
    stages{
        stage('Checkout SCM'){
            steps{
                checkout scm
            }
        }
        stage('Build FrontEnd'){
            steps{
                //sh './mvnw'
                sh 'npm install'
                sh 'npm build'
            }

        }
        stage('Build BackEnd'){
            steps{
                sh 'mvn package'
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
            
        }

    }
}