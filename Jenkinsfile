pipeline {

  agent any

  stages {

    
      stage("Build image") {
            steps {
                script {
                    myapp = docker.build("androshchuk/hellowhale:latest")
                }
            }
        }
    
      stage("Push image") {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {                           
                            myapp.push("latest")
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
