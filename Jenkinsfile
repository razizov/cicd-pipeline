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
        BUILD_NUMBER = '1'
      }
      steps {
        sh '''script {
docker.withRegistry(\'https://registry.hub.docker.com\', \'dockerhub\')  




{ 
app.push("${env.BUILD_NUMBER}") 
app.push("latest") 
}
}
'''
        }
      }

    }
  }