pipeline {
  agent any 
  stages {
     stage('Initialize'){
        steps{
            script{
                def dockerHome = tool 'myDocker'
                env.PATH = "${dockerHome}/bin:${env.PATH}"

            }
        }
    }
    stage('Verify version') {
      steps {
        sh 'sudo docker run --rm flyway/flyway:8.5.1 version'
      }
    }
  }
}