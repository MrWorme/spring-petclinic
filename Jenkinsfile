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
                slackSend "Build Success "
       }
       failure {
                slackSend "Build Failure"
       }
       always {
                slackSend "Build did"
       }
    }
}
