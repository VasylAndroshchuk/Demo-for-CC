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
     sh "sed -ie "s/THIS_STRING_IS_REPLACED_DURING_BUILD/$(date)/g" app.yml"
     sh "kubectl apply -f lamp"
     sh "kubectl apply -f app.yaml"
    
}
            
            }
        }
    
    

  }

}
