pipeline {

   agent any
    environment {
        DOCKER_USERNAME = credentials('DOCKER_USERNAME')
        DOCKER_PASSWORD = credentials('DOCKER_PASSWORD')
    }
   stages {

       stage('docker-compose') {
           steps {
              sh "docker-compose down || true"
              sh "docker system prune -a -f"
              sh "docker-compose --verbose up -d"
              sh "ls -ltra"
           }
       }
      
       stage('docker-login') {
           steps {
               script {
                  docker.withRegistry( '', 'DOCKER_USERNAME' ) {
                     sh: "docker push dpage/pgadmin4:latest"
                  }
               }
           }
       }
      
       stage('docker-push') {
           steps {
              sh "docker image tag postgres:11 psalmprax/postgres:latest
"
              sh: "docker push psalmprax/postgres:latest"
           }
       }
   }
   post {
      always {
         sh "docker system prune -a -f"
         sh "docker-compose ps"
      }
   }   
}
