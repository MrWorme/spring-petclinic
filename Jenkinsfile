pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                bat './mvnw clean' 
            }
        }
        stage('Test') {
            steps {
                bat './mvnw test' 
            }
        }
        stage('Package') {
            steps {
                bat './mvnw package' 
            }
        }
        stage('Deploy') {
            when { branch 'master'}
                steps {
                    bat './mvnw deploy' 
                }                   
        }
    }
    post {
       success {
                slackSend  message: "Build Success "
       }
       failure {
                slackSend  message: "Build Failure"
       }
       always {
                slackSend  message: "Build did"
       }
    }
}
