pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/aftab-s/Jenkins-101', branch: 'main')
      }
    }

    stage('Simple Logging') {
      parallel {
        stage('Simple Logging') {
          steps {
            sh 'ls -la'
          }
        }

        stage('Frontend Unit Test') {
          steps {
            sh 'cd curriculum-app/curriculum-front && npm i && npm run test:unit'
          }
        }

      }
    }

    stage('Frontend Build') {
      steps {
        sh 'docker build -f curriculum-app/curriculum-front/Dockerfile .'
      }
    }

  }
}