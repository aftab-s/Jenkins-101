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

        stage('Install Global Dependancies') {
          steps {
            sh 'npm -v || sudo su && (apt-get install -y nodejs npm)'
          }
        }

        stage('Install Project Dependencies') {
          steps {
            sh 'npm install'
          }
        }

      }
    }

    stage('Frontend Build') {
      steps {
        sh 'cd curriculum-app/curriculum-front && docker build -t app-v1 .'
      }
    }

  }
}