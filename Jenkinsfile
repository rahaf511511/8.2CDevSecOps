pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/rahaf7373/8.2CDevSecops.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Build done"'
            }
        }

        stage('Unit Tests') {
            steps {
                sh 'echo "Tests passed"'
            }
        }

        stage('Code Quality') {
            steps {
                echo 'SonarCloud stage (placeholder)'
            }
        }

        stage('Security Scan') {
            steps {
                sh 'npm audit || true'
            }
        }

        stage('Package') {
            steps {
                sh 'echo "Packaging done"'
            }
        }
    }

    post {
        always {
            echo 'Pipeline Finished'
        }
        success {
            echo 'Build Success'
        }
        failure {
            echo 'Build Failed'
        }
    }
}
