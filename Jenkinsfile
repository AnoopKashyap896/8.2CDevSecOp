pipeline {
    agent any
     triggers {
         // Poll every minute for simulation purpose
        pollSCM('* * * * *') 
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: ' https://github.com/AnoopKashyap896/8.2CDevSecOp.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                bat 'npm test || exit /b 0'
            }
        }
        stage('Generate Coverage Report') {
            steps {
                bat 'npm run coverage || exit /b 0'
            }
        }
        stage('NPM Audit (Security Scan)') {
            steps {
                bat 'npm audit || exit /b 0'
            }
        }
    }
}
