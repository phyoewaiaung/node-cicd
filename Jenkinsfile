pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Install') {
      steps {
        sh 'npm install'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t node-cicd-app .'
      }
    }

    stage('Deploy') {
      steps {
        sh 'docker stop node-cicd-container || true'
        sh 'docker rm node-cicd-container || true'
        sh 'docker run -d --name node-cicd-container -p 3000:3000 node-cicd-app'
      }
    }
  }
}