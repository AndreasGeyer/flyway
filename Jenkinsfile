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
        sh 'ls'
        sh 'pwd'
        sh 'docker run --rm -v ./jenkins:/flyway/sql --network Jenkinsnetwork flyway/flyway -url=jdbc:postgresql://db-dev:5432/postgres -user=postgres -password=example migrate'
      }
    }
  }
}
