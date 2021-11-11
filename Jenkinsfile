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

        stage('Test Log') {
          steps {
            writeFile(file: 'testoutput', text: 'This is automation file')
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
  environment {
    VAGRANT_USER = 'vagrant'
  }
}