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
                            myapp.push("latest")
                            myapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }

    
    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "app.yaml", kubeconfigId: "mykubeconfig")
        }
      }
    }

  }

}
