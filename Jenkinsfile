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
        
       stage('Push Image') {
           
          steps{
          script {
              
            docker.withRegistry( '', registryCredential ) {
                 dockerImage.push()
                 
                                                            }
                 }
                 }
                            }    
                
        stage('Run Image'){
              
              steps{
                  script{
                  sh 'docker run $registry:latest'
                  }
              }
              }
              
              
              
              
      }  
    }
