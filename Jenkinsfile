pipeline {
  agent any
  stages {
    stage('build & unit tests') {
      steps {
        sh 'echo "build & unit tests"'
        sleep(time: '5', unit: 'SECONDS')
      }
    }
    stage('static-analysis') {
      steps {
        sh 'echo "static-analysis"'
        sleep(time: '5', unit: 'SECONDS')
      }
    }
    stage('acceptance-tests') {
      steps {
        parallel(
          "chrome": {
            sh 'echo "chrome"'
            sleep(time: '5', unit: 'SECONDS')
          },
          "edge": {
            sh 'echo "edge"'
            sleep(time: '5', unit: 'SECONDS')

          },
          "firefox": {
            sh 'echo "fire"'
            sleep(time: '5', unit: 'SECONDS')

          }
        )
        
      }
    }
    stage('staging') {
      steps {
        sh 'echo "staging"'
        sleep(time: '5', unit: 'SECONDS')
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
        sleep(time: '5', unit: 'SECONDS')
      }
    }
  }
}
