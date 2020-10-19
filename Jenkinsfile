pipeline {
   agent any {
   tools {git 'git'}
   environment
    {
       VERSION = "${BUILD_NUMBER}"
       REPOSITORY_PREFIX='madavi'
       registry = "amm123/tomcat"
       registryCredential = 'dockerhub'
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
} 
