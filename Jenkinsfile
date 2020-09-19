pipeline {
    environment {
registry = "nainikachowdary/java_app"
registryCredential = 'docker123'
dockerImage = ''
}
    agent none
    stages {
        stage('Build') { 
            agent any
             steps {
                sh 'mvn install'
            }
            }
       
       stage ('dockerization') {
           agent any
            steps{
              script {
              dockerImage = docker.build("nainikachowdary/java_app")
                }
                 }
       }
       stage('Deploy Image') {
           agent any
          steps{
          script {
              
            withDockerRegistry([ credentialsId: "docker123", url: "" ]) {
                 dockerImage.push("${env.BUILD_NUMBER}")
                 dockerImage.push("latest")
            }
    }
  }
}    
                
             
        }
        
    }
