pipeline {
    environment {
registry = "nainikachowdary/java_app2"
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
              script {
              dockerImage = docker.build(registry)
                }
                 }
       }
       stage('Deploy Image') {
           
          steps{
          script {
              
            docker.withRegistry( '', registryCredential ) {
                 dockerImage.push("${env.BUILD_NUMBER}")
                 dockerImage.push("latest")
            }
    }
  }
}    
                
             
        }
        
    }
