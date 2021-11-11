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
            echo "get user ${VAGRANT_USER}"
          }
        }

        stage('Test Log') {
          steps {
            writeFile(file: 'logtestfile.txt', text: "This is automation file log for ${VAGRANT_USER}")
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            echo 'Deploying  to Azure'
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