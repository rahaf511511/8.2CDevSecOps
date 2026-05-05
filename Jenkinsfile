pipeline {
    agent any

    environment {
        SONAR_SCANNER_VERSION = '8.0.1.6346'
        SONAR_SCANNER_HOME = "${WORKSPACE}/sonar-scanner-8.0.1.6346-linux-aarch64"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/rahaf511511/8.2CDevSecOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install || true'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'echo "Skipping tests for this task"'
            }
        }

        stage('NPM Audit') {
            steps {
                sh 'npm audit || true'
            }
        }

        stage('Create SonarCloud Config') {
            steps {
                writeFile file: 'sonar-project.properties', text: '''
sonar.projectKey=rahaf511511_8.2CDevSecOps
sonar.organization=rahaf511511
sonar.host.url=https://sonarcloud.io
sonar.sources=.
sonar.exclusions=node_modules/**,coverage/**,sonar-scanner-*/**,**/*.min.js,public/**,views/**
sonar.javascript.node.maxspace=4096
'''
            }
        }

        stage('SonarCloud Analysis') {
            steps {
                withCredentials([string(credentialsId: 'SONAR_TOKEN', variable: 'SONAR_TOKEN')]) {
                    sh '''
                    rm -rf sonar-scanner-* sonar-scanner.zip
                    curl -L -o sonar-scanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-8.0.1.6346-linux-aarch64.zip
                    unzip -o sonar-scanner.zip
                    chmod +x sonar-scanner-8.0.1.6346-linux-aarch64/bin/sonar-scanner
                    ./sonar-scanner-8.0.1.6346-linux-aarch64/bin/sonar-scanner -Dsonar.token=$SONAR_TOKEN
                    '''
                }
            }
        }
    }
}
