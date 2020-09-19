pipeline {
    
    environment {
registry = "nainikachowdary/java_app1"
registryCredential = 'docker123'
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
                script{
                    dockerImage = docker.build("nainikachowdary/java_app1")
                }
                 }
       }
       stage('Deploy Image') {
           
          steps{
          
              withDockerRegistry([ credentialsId: "docker123", url: "" ])
             {  sh '''docker push brightbox/terraform:latest
                 docker push brightbox/cli:latest'''
              script {
                  dockerImage.push("${env.BUILD_NUMBER}")
                 dockerImage.push("latest")
              }
             }   
            
    
  }
}    
                
             
        }
        
    }
