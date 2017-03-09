pipeline {
  agent any
  stages {
    stage('build & unit tests') {
      steps {
        sh 'echo "build and unit tests"'
        sleep 5
      }
    }
    stage('static-analysis') {
      steps {
        sh 'echo "static-analysis"'
        sleep 5
      }
    }
    stage('acceptance-tests') {
      steps {
        parallel(
          "chrome": {
            sh 'echo "chrome"'
            sleep 5
          },
          "edge": {
            sh 'echo "edge"'
            sleep 5

          },
          "firefox": {
            sh 'echo "fire"'
            sleep 5

          }
        )
        
      }
    }
    stage('staging') {
      steps {
        sh 'echo "staging"'
        sleep 5
      }
    }
    stage('manual-approval') {
      steps {
        input 'Want to continue ?'
      }
    }
    stage('deploy') {
      steps {
        sh 'echo "deploy"'
        sleep 5
      }
    }
  }
}
