pipeline {
    agent any

    stages {

        stage('1. Checkout Code') {
            steps {
                git url: 'https://github.com/rahaf7373/8.2CDevSecops.git'
            }
        }

        stage('2. Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('3. Build') {
            steps {
                sh 'echo "No build step required (or replace with npm run build)"'
            }
        }

        stage('4. Unit Tests') {
            steps {
                sh 'npm test || true'
            }
        }

        stage('5. Code Quality (SonarCloud)') {
            steps {
                sh 'echo "SonarCloud step goes here (to be configured)"'
            }
        }

        stage('6. Security Scan') {
            steps {
                sh 'npm audit || true'
            }
        }

        stage('7. Package') {
            steps {
                sh 'zip -r app.zip . || true'
            }
        }
    }

    post {
        always {
            echo 'Pipeline Finished'
        }
        success {
            echo 'Build Successful'
        }
        failure {
            echo 'Build Failed'
        }
    }
}
