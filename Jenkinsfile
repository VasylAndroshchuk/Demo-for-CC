pipeline {

  agent any

  stages {

    stage('Checkout Source') {
      steps{
        script {
          checkout scm
        }
      }
    }

    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build("androshchuk/hellowhale:${env.BUILD_ID}")
        }
      }
    }

    stage('Push Image') {
      steps{
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            dockerImage.push("latest")
          }
        }
      }
    }

    stage('Deploy App') {
      steps {

          withCredentials([file(credentialsId: 'mykubeconfig', variable: 'mykubeconfig')]) {
            sh 'kubectl apply -f app.yaml'
            
        }
      }
    }
  }
}
