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
            echo 'get vagrant user "$VAGRANT_USER"'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'deploying  to azure'
      }
    }

  }
  environment {
    VAGRANT_USER = 'vagrant'
  }
}