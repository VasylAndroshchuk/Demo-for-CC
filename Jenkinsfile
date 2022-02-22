pipeline {

  agent any

  stages {

    
      stage("Build image") {
            steps {
                script {
                    myapp = docker.build("androshchuk/hellowhale:${env.BUILD_ID}")
                }
            }
        }
    
      stage("Push image") {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {                           
                            myapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }

            stage('Deploy') {
            steps {
                withAWS(credentials: 'AWS_CRED') {
     sh "kubectl apply -f lamp"
     sh "kubectl apply -f app.yaml"
    
}
            
            }
        }
    
    

  }

}
