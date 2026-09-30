pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps { checkout scm }
    }
    stage('Build Image') {
      steps { sh 'docker build -t hello-python:${BUILD_NUMBER} .' }
    }
    stage('Test') {
      steps { sh 'docker run --rm hello-python:${BUILD_NUMBER} python -m pytest' }
    }
    stage('Run') {
      steps { sh 'docker run --rm hello-python:${BUILD_NUMBER}' }
    }
  }

  post {
    success { echo 'SUCCESS' }
    failure { echo 'FAILED' }
  }
}