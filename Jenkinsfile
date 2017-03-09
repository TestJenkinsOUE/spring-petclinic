pipeline {
  agent any
  stages {
    stage('build & unit tests') {

      steps {
        sh 'echo "build and unit tests"'
        sleep 5
        withMaven(
                    maven: 'M3' // Maven installation declared in the Jenkins "Global Tool Configuration"
                    //mavenSettingsConfig: 'settings.xml' // Maven settings.xml file defined with the Jenkins Config File Provider Plugin => à ajouter directement sur jenkins : Manage Jenkins > Managed files > Add a new Config > 
                    ) {

                  // Run the maven build
                  sh "mvn clean install"

                }
        /**withMaven(globalMavenSettingsConfig: 'GlobalMavenSettingsConfig', globalMavenSettingsFilePath: 'GlobalMavenSettingsFilePath', jdk: 'Jdk', maven: 'Maven', mavenLocalRepo: 'MavenLocalRepo', mavenOpts: 'MavenOpts', mavenSettingsConfig: 'MavenSettingsConfig', mavenSettingsFilePath: 'MavenSettingsFilePath')*/
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
