pipeline {
environment {
imagename = "jigyasumishra321/my-app"
registryCredential = 'jigyasumishra321-dockerhub'
dockerImage = ''
}
agent any
stages {
stage('Cloning Git') {
steps {
sh 'rm -rf *'
sh 'git clone git@github.com:jigyasumishra321/Jenkinsfile1.git'
}
}
stage('Building image') {
steps{
script {
dockerImage = docker.build imagename
}
}
}
stage('Deploy Image') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
dockerImage.push("$BUILD_NUMBER")
dockerImage.push('latest')
}
}
}
}
stage('Remove Unused docker image') {
steps{
sh "docker rmi $imagename:$BUILD_NUMBER"
sh "docker rmi $imagename:latest"
}
}
}
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}
