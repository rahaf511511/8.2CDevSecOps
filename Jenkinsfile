pipeline {
  agent any

  stages {

    stage('Build') {
      steps {
        sh 'npm install'
      }
    }

    stage('Unit Tests') {
      steps {
        sh 'npm test'
      }
    }

    stage('Code Analysis') {
      steps {
        echo 'Running Code Analysis'
      }
    }

    stage('Security Scan (Snyk)') {
      steps {
        sh 'snyk test || true'
      }
    }

    stage('Deploy to Staging') {
      steps {
        echo 'Deploying to staging...'
      }
    }

    stage('Integration Tests') {
      steps {
        echo 'Running integration tests...'
      }
    }

    stage('Deploy to Production') {
      steps {
        echo 'Deploying to production...'
      }
    }

  }
}
