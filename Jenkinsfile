pipeline {
  agent any
  tools {
    maven 'maven' 
  }
  stages {
    stage('GetCode'){
      steps{
        git 'https://github.com/shaik-haneef001/Hello.git'
      }
    }
    stage ('Build') {
      steps {
        sh 'mvn clean compile test package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'Deployer', path: '', url: 'http://13.211.238.20:8080/')], contextPath: '/pipeline', onFailure: false, war: 'webapp/target/*.war' 
        }
      }
    }
  }
}
