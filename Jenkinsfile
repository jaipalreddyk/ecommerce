pipeline {
  agent any
  stages {
    stage('code pull') {
      steps {
        git 'https://github.com/krishna7362/ecommerce.git'
      }
    }
    stage('build') {
      steps {
        bat 'C:\\apache-maven-3.6.1\\bin\\mvn install'
      }
    }
    stage('junit') {
      steps {
        bat 'C:\\apache-maven-3.6.1\\bin\\mvn test'
      }
    }
    stage('sonarqube') {
      steps {
        bat 'C:\\apache-maven-3.6.1\\bin\\mvn sonar:sonar'
      }
    }
    stage('deploy') {
      steps {
        bat 'xcopy "C:\\Program Files (x86)\\Jenkins\\workspace\\ecommerce_master\\target\\ecommerce.war"  "C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\webapps" && Yes'
      }
    }
  }
}