pipeline {
  environment {
    registry = "akhilreddy0428/ci-cd-pipeline"
    //registryCredential = `DockerCreds`
    dockerImage = ''
  }  
agent any
stages {
  stage('Cloning our Git') {
    steps {
      script{
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
   	  // This step should not normally be used in your script. Consult the inline help for details.
withDockerRegistry(credentialsId: 'DockerCreds') {
    // some block
         
 //docker.withRegistry( '', registryCredential )
            dockerImage.push()
          }
        }
      }
    }
    stage('Deploy to kubernetes'){
        steps{
          script{
                      kubernetesDeploy(configs: "myweb.yaml", kubeconfigId: "Azure-k8s-kubeconfig")
          }
        }
      }
   }
}
