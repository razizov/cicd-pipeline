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
        sh 'docker build -t rishatazizov/cicdtest .'
      }
    }

    stage('Docker image push') {
      environment {
        USER = 'rishatazizov'
        PASS = 'jyvgyd-tUqmew-qupmo8'
      }
      steps {
        sh '''docker login -u $USER -p $PASS
docker image push rishatazizov/cicdtest:latest
'''
      }
    }

  }
}