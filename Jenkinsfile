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

  }
}