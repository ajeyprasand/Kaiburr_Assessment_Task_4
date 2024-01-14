pipeline {
agent any
  stages {
    stage('Checkout') {
      steps {
          git branch: 'main', url: 'https://github.com/ajeyprasand/Kaiburr_Assessment_Task_3.git'
      }
    }
    stage('Build and Test') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Static Code Analysis') {
      environment {
        SONAR_URL = "http://localhost:9090"
      }
      steps {
        withCredentials([string(credentialsId: 'Sonar-Token', variable: 'SONAR_AUTH_TOKEN')]) {
          sh 'mvn sonar:sonar -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL}'
        }
      }
    }

  }
}
