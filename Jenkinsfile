pipeline {
    agent any
    environment{
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Build Stage'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Test Stage'
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deleiver for Development') {
            when{
                branch 'development'
            }
            steps {
                echo 'Development Stage'
                sh './jenkins/scripts/deliver-for-development.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
        stage('Deleiver for Production') {
            when{
                branch 'production'
            }
            steps {
                echo 'Production Stage'
                sh './jenkins/scripts/deliver-for-production.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
