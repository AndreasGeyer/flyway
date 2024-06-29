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
        sh 'cd /var/jenkins_home/workspace/test2/jenkins'
        sh 'ls'
        sh 'pwd'
        sh 'docker run --rm -v /var/jenkins_home/workspace/test2/jenkins:/flyway/sql --network Jenkinsnetwork flyway/flyway -url=jdbc:postgresql://db-dev:5432/postgres -user=postgres -password=example migrate'
      }
    }
  }
}
