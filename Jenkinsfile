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
              
                 sh 'docker build -t nainikapanguluri/java_app2 .'
                
                 }
       }
       stage('Deploy Image') {
           
          steps{
          
              withDockerRegistry([ credentialsId: "docker-hub", url: "" ])
             {  sh '''docker push brightbox/terraform:latest
                 docker push brightbox/cli:latest
                docker push nainikapanguluri/java_app2'''
                
            }
    
  }
}    
                
             
        }
        
    }
