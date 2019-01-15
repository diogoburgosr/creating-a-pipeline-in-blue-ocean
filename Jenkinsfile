pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3001:3000'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '''npm config set proxy http://10.0.101.43:3128
npm config set https-proxy http://10.0.101.43:3128
npm install'''
      }
    }
    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
  }
}