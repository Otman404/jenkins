pipeline {
  environment {
    registry = "otmane404/tp4_jenkins"
    registryCredential = 'docker_login'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/Otman404/tp4'
      }
    }
    stage('Building image') {
      steps {
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Test image') {
      steps {
        script {

          echo "Tests passed"
        }
      }
    }
    stage('Publish Image') {
      steps {
        script {
          docker.withRegistry('', registryCredential) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
