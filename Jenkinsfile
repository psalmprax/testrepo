pipeline {

   agent any

   stages {
       stage('docker-compose') {
           steps {
              sh "ls -ltra"
              sh "sudo docker-compose up -d"
              
           }
       }
   }
   post {
      always {
         sh "sudo docker-compose down || true"
      }
   }   
}
