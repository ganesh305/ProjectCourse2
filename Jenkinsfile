pipeline{
   agent {
       label 'master'
   }
 
  
   tools {
       maven 'maven3'
       jdk 'jdk11'
   }
 

  stages{
 
   stage('Copy War file for build the image'){
          steps {
              script {
              sh """
                cp -r /var/lib/jenkins/workspace/Pipeline2/target/addressbook-2.0.war .
              """
              }
       
          }
      }
    
  
    stage('Build the image using dockerfile'){
          steps {
              script {
              sh """
              cp -rf /home/ganeshps403gmai/dockerfl/Dockerfile .
              """
              }
              sh 'docker build -t ganesh403/addressbook-devops:v1 .'
 
       
          }
      }
    stage('Loging into Dockerhub'){
          steps {
             
              sh 'docker login -u ganesh403  -p Pass@7089'
       
          }
      }
    stage('Push the image'){
          steps {
             
              sh 'docker push  ganesh403/addressbook-devops:v1'
       
          }
      }
    stage('Deploy the application'){
          steps {
             
        sh 'docker run -td -P  ganesh403/addressbook-devops:v1'
       
          }
      }
  }
 
}
