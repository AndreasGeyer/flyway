pipeline {
  agent any 
  stages {
    stage('Verify Docker version') {
      steps {
        sh 'docker version'
      }
    }
    stage('Execute DB Changes on DEV') {
        when {
            branch 'development'
        }
        steps {
        echo 'Run Flyway Migration'
        sh '''
                cd /var/jenkins_home/workspace/test2/mysqlfiles
                ls -al
                pwd
                '''
        sh 'docker run --rm -v /Users/andreasgeyer/jenkins/workspace/test2/mysqlfiles:/flyway/sql --network Jenkinsnetwork flyway/flyway -url=jdbc:postgresql://db-dev:5432/postgres -user=postgres -password=example migrate'
      }
    }
    stage('Deploy to INT') {
        when {
            branch 'integration'
        }
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
    stage('Deploy to ACC') {
        when {
            branch 'acceptance'
        }
        steps {
        echo 'Run Flyway Migration'
        sh '''
                cd /var/jenkins_home/workspace/test2/mysqlfiles
                ls -al
                pwd
                '''
        sh 'docker run --rm -v /Users/andreasgeyer/jenkins/workspace/test2/mysqlfiles:/flyway/sql --network Jenkinsnetwork flyway/flyway -url=jdbc:postgresql://db-acc:5432/postgres -user=postgres -password=example migrate'
      }
    }
    stage('Deploy to Production') {
        when {
            branch 'main'
        }
        steps {
        echo 'Run Flyway Migration'
        sh '''
                cd /var/jenkins_home/workspace/test2/mysqlfiles
                ls -al
                pwd
                '''
        sh 'docker run --rm -v /Users/andreasgeyer/jenkins/workspace/test2/mysqlfiles:/flyway/sql --network Jenkinsnetwork flyway/flyway -url=jdbc:postgresql://db-prod:5432/postgres -user=postgres -password=example migrate'
      }
    }
  }
}
