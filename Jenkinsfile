pipeline {

   agent any

   stages {

       stage('docker-compose') {
           steps {
              sh "docker-compose --verbose down || true"
              sh "docker-compose --verbose up -d"
              sh "ls -ltra"
           }
       }
   }
   post {
      always {
         sh "docker-compose --verbose ps"
      }
   }   
}
