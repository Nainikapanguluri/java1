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
              agent {
        label 'worker-linux'
    }
              steps{
                  script{
                  sh 'docker run -t -p 8081:8080 $registry:latest'
                  }
              }
              }
              
              
              
              
      }  
    }
