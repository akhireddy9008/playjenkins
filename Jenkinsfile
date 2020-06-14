pipeline {
environment {
registry = "akhilreddy0428"
registryCredential = 'DockerCreds'
dockerImage = ''
}
agent any
stages {
stage('Cloning our Git') {
steps {
git 'hps://github.com/akhireddy9008/pipeline-demo-2.git'
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
}
