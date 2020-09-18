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
              script {
              dockerImage = docker.build("nainikapanguluri/java_app1")
                }
                 }
       }
       stage('Deploy Image') {
           
          steps{
          script {
              docke.push(brightbox/terraform)
              docker.push(brightbox/cli)
              withDockerRegistry([ credentialsId: "docker-hub", url: "" ])
             {
                 dockerImage.push("${env.BUILD_NUMBER}")
                 dockerImage.push("latest")
            }
    }
  }
}    
                
             
        }
        
    }
