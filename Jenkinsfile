pipeline {
    
    environment {
registry = "nainikapanguluri/java_app1"
registryCredential = 'docker-hub'
dockerImage = ''
}
    agent any
    stages {
        stage('Build') { 
            
             steps {
                sh 'mvn install'
            }
            }
        
       stage ('dockerization') {
           
            steps{
              sh 'dockerImage = docker.build("nainikapanguluri/java_app1")'
              
                 }
       }
       stage('Deploy Image') {
           
          steps{
          
              withDockerRegistry([ credentialsId: "docker-hub", url: "" ])
             {  sh '''docker push brightbox/terraform:latest
                 docker push brightbox/cli:latest
                 dockerImage.push("${env.BUILD_NUMBER}")
                 dockerImage.push("latest")'''
             }   
            
    
  }
}    
                
             
        }
        
    }
