pipeline {

   agent any

   stages {
      stage("Fix the permission issue") {
            agent any
            steps {
                sh "chown root:jenkins /run/docker.sock"
            }

        }
       stage('docker-compose') {
           steps {
              sh "docker-compose --verbose up -d"
              sh "ls -ltra"
           }
       }
   }
   post {
      always {
         sh "docker-compose down || true"
      }
   }   
}
