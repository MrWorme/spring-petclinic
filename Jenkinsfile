pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                slackSend "Build Started - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
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
}
