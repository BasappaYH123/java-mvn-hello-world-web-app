pipeline {
  agent {label 'jenkins_slave1'}
  stages {
   
stage ('build'){
      steps{
        sh 'pwd'
        sh 'ls'
        sh 'docker build -t mvn1:latest .'
      }
    }
     stage ('publish'){
      steps{
        sh 'docker tag mvn1:latest basappayh/mvnnow:5.0'
        sh 'docker login -u basappayh -p Welcome@123'
        sh 'docker push basappayh/mvnnow:5.0'
      }
    }
  stage ('deploy'){
     agent {label 'jenkins_slave2'}
      steps{
        sh 'docker login -u basappayh -p Welcome@123'        
        sh 'docker pull basappayh/mvnnow:5.0'
        sh 'docker run -d -p 7001:8080 basappayh/mvnnow:5.0'
      }
    }  
  }
}
  

