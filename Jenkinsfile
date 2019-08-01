pipeline {
  agent any
  stages {
    stage('CodePull') {
      steps {
        git 'https://github.com/krishna7362/ecommerce.git'
      }
    }
    stage('Build') {
      steps {
        bat 'mvn clean install'
      }
    }
  }
}