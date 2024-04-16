pipeline {
  agent any 
  stages {
    stage('Verify Docker version') {
      steps {
        sh 'id -g'
        sh 'id -G'
        sh 'groups'
        sh 'docker version'
      }
    }
  }
}