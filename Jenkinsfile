pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Building Docker image'
          }
        }

        stage('Test') {
          steps {
            echo 'Testing application'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'deploying  to Azure'
      }
    }

  }
}