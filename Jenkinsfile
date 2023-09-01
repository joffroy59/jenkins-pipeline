pipeline {
  agent any
  stages {
    stage('Init') {
      steps {
        sh 'echo "Stage 1 - Step1"'
      }
    }

    stage('Parallel1') {
      parallel {
        stage('Parallel1') {
          steps {
            echo 'Parallel 1 -Step 1'
          }
        }

        stage('Parallel 2') {
          steps {
            echo 'Parallel 2 -Step 1'
          }
        }

      }
    }

    stage('End') {
      steps {
        echo 'End'
      }
    }

  }
}