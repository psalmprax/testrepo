pipeline {

   agent any

   stages {
       stage('docker-compose') {
           steps {
              sh "ls -ltra"
              sh "docker-compose up -d"
              
           }
       }
   }
   post {
      always {
         sh "docker-compose down || true"
      }
   }   
}
