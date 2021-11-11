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
            writeFile(file: 'logtestfile.txt', text: 'This is automation file log')
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            echo 'deploying  to Azure'
          }
        }

        stage('Artifacts') {
          steps {
            archiveArtifacts 'logtestfile.txt'
          }
        }

      }
    }

  }
  environment {
    VAGRANT_USER = 'vagrant'
  }
}