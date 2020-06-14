pipeline {

#  environment {
 #   registry = "192.168.1.81:5000/justme/myweb"
 #   dockerImage = ""
 # }
environment {
registry = "akhilreddy0428"
registryCredential = 'DockerCreds'
dockerImage = ''
}
  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/akhireddy9008/pipeline-demo-2.git'
      }
    }
}
    stage('Building our image') {
steps{
script {
dockerImage = docker.build registry + ":$BUILD_NUMBER"
}
}
}
stage('Deploy our image') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
dockerImage.push()
}
}
}
}
}
#    stage('Deploy App') {
 #     steps {
  #      script {
   #       kubernetesDeploy(configs: "myweb.yaml", kubeconfigId: "azure-kube-config")
    #    }
     # }
    #}

  
#}

#}
