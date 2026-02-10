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
    }
}
