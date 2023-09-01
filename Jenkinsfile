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

        stage('checkout git') {
          steps {
            git(url: 'https://github.com/joffroy59/git-blank.git', branch: 'main', credentialsId: 'github-joffroy59', changelog: true)
          }
        }

        stage('Launch other job - changelog ') {
          steps {
            script {
              jobLaunch = build(job: 'Changelog', propagate: true, wait: true)
            }

          }
        }

        stage('wait buid ok') {
          steps {
            waitForBuild(runId: '${jobLaunch.id}', propagate: true)
            echo 'job ended'
          }
        }

      }
    }

    stage('End') {
      parallel {
        stage('End') {
          steps {
            echo 'End'
          }
        }

        stage('publish ') {
          steps {
            echo 'fff'
          }
        }

      }
    }

    stage('test') {
      steps {
        waitForBuild jobLaunch.id
      }
    }

  }
}