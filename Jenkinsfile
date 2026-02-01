pipeline {
    agent any
stages {
   stage('checkout') {
      steps {
          git branch :https://github.com/studentmaterial02-create/java.git
          }
      }
   stage('Build') {
      steps {
         sh 'mvn clean package'
      }
   }
    stage('Docker Build') {
       steps {
         sh 'docker build -t parkar05/java-app:latest .'
         }
      }
    stage('Docker push') {
       steps {
         sh 'docker push parkar05/java-app:latest'
         }
      }
    stage('Deploy to kubernetes') {
       steps {
          sh 'kubectl apply -f k8s/'
         }
      }
   }
}
