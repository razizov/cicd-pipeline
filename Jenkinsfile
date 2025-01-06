pipeline {
  agent any
  stages {
    stage('Git checkout') {
      steps {
        git(url: 'https://github.com/razizov/cicd-pipeline.git', branch: 'main')
      }
    }

    stage('Application build') {
      steps {
        sh 'script scripts/build.sh'
      }
    }

    stage('Tests') {
      steps {
        sh 'script scripts/test.sh'
      }
    }

    stage('Docker image build') {
      steps {
        sh 'docker build -t razizov-cicd'
      }
    }

  }
}