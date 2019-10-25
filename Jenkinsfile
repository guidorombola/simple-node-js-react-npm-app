pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3001:3000' 
        }
    }
    environment {
        CI = 'true'
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
        stage('Deliver') { 
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
    
}
