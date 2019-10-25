pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3001:3000' 
        }
    }
    triggers {
        cron('*/5 * * * *')
    }
    stages {
        stage('Install') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Build') { 
            steps {
                sh 'npm build' 
            }
        }
        stage('Test') { 
            steps {
                sh 'npm test' 
            }
        }
    }
    
}
