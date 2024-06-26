pipeline {
  agent any 
  stages {
    stage('Verify Docker version') {
      steps {
        sh 'docker version'
      }
    }
    stage('Deploy Changes to DB') {
      steps {
        echo 'Run Flyway Migration'
        echo "${WORKSPACE}"
        sh 'whereis flyway'
        sh 'flyway info'
      }
    }
  }
}