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
        sh '''
                cd /var/jenkins_home/workspace/test2/mysqlfiles
                ls -al
                pwd
                '''
        sh 'docker run --rm -v /Users/andreasgeyer/jenkins/workspace/test2/mysqlfiles:/flyway/sql --network Jenkinsnetwork flyway/flyway -url=jdbc:postgresql://db-int:5432/postgres -user=postgres -password=example migrate'
      }
    }
  }
}
