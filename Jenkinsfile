pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/aftab-s/Jenkins-101', branch: 'main')
      }
    }

    stage('Setup Environment') {
      steps {
        script {
          // Check if npm is installed, if not, fail the build.
          def npmInstalled = sh(script: 'command -v npm', returnStatus: true) == 0
          if (!npmInstalled) {
            error("npm is not installed. Ensure Node.js and npm are installed on the Jenkins agent.")
          }
        }
      }
    }

    stage('Install Global Dependencies') {
      steps {
        sh 'npm install -g some-global-dependency' // Example of installing a global dependency if needed
      }
    }

    stage('Install Project Dependencies') {
      steps {
        // Install project dependencies after checking out the code
        sh 'cd curriculum-app/curriculum-front && npm install'
      }
    }

    stage('Run Simple Logging') {
      parallel {
        stage('Simple Logging') {
          steps {
            sh 'ls -la'
          }
        }

        stage('Frontend Unit Tests') {
          steps {
            sh 'npm run test:unit'
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
