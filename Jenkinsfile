pipeline {
  agent any
  tools {
    maven 'maven-3.8.6' 
  }
  stages {
    stage('GetCode'){
      steps{
        git 'https://github.com/shaik-haneef001/Hello.git'
      }
    }
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'Deployer', path: '', url: 'http://13.211.238.20:8080/')], contextPath: '/pipeline', onFailure: false, war: '/var/lib/jenkins/workspace/Compile-Test-Package/webapp/target/webapp.war' 
        }
      }
    }
  }
}