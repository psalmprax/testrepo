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
   }
   post {
      always {
         sh "DOCKER_USERNAME=psalmprax && DOCKER_PASSWORD=Single123."
         sh "docker login -u='${DOCKER_USERNAME}' -p='${DOCKER_PASSWORD}'"
         sh "docker system prune -a -f"
         sh "docker-compose ps"
      }
   }   
}
