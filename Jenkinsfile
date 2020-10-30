pipeline {
   agent any
   tools {git 'git'}
   environment
    {
       VERSION = "${BUILD_NUMBER}"
       REPOSITORY_PREFIX='madavi'
       registry = "9492489757/satish1"
       registryCredential = 'docker'
       dockerImage = ''
   }
   
   stages {
     stage('checkout') {
          steps {
           
               git url: 'https://github.com/inspired123/CI-CD-using-Docker.git'
           
       }
       }
     stage('Image Build'){
          steps{
              script{
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
 
