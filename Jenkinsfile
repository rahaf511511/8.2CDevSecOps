pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Building project...'
            }
        }

        stage('Unit Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Security Scan (Snyk)') {
            steps {
                sh 'snyk test || true'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'SonarCloud placeholder'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
            }
        }

    }
}
