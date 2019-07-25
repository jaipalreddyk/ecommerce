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
        bat 'runapp.bat'
      }
    }
    stage('Email')
        {
            env.ForEmailPlugin = env.WORKSPACE      
            emailext attachmentsPattern: 'TestResults\\*.trx',      
            body: '''${SCRIPT, template="groovy_html.template"}''', 
            subject: currentBuild.currentResult + " : " + env.JOB_NAME, 
            to: 'priya52krishna@gmail.com'
        }
  }
  
  
}
