pipeline {

  agent any

  stages {

    
      stage("Build image") {
            steps {
                script {
                    myapp = docker.build("androshchuk/hellowhale:latest")
                  telegramSend 'Hello World'
                }
            }
        }
    
      stage("Push image") {
            steps {
                script {
                    sh "curl -s -X POST https://api.telegram.org/bot[5162489196:AAHm2P6UIIuqBmZCo0Y2-ylWoD9XWecwVCw]/sendMessage -d chat_id=[477851445] -d text="Push done""
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
