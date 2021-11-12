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
          environment {
            LocalVariable = 'HelloLocal'
          }
          steps {
            writeFile(file: 'logtestfile.txt', text: "This is automation file log for ${VAGRANT_USER} and local var is : ${LocalVariable}")
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('Deploy') {
          when {
            branch 'master'
        }
          steps {
            input(message: 'Do you want to deploy', id: 'OK')
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