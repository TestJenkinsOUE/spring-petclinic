pipeline {

    stage('build & unit tests') {
        node("build") {
            echo 'build & unit tests'
            sleep 5
        }


    }
    stage('static-analysis') {
        node("build") {
            echo 'static-analysis'
            sleep 5
        }

    }
    stage('acceptance-tests') {
        echo 'acceptance-tests'
        parallel(
                "chrome": {
                    node("build") {
                        echo "chrome"
                        sleep 5
                    }

                },
                "edge": {
                    node("build") {
                        echo "edge"
                        sleep 5
                    }

                },
                "firefox": {
                    node("build") {
                        echo "firefox"
                        sleep 5
                    }

                }

        )
    }

    stage('staging') {
        node("build") {
            echo 'staging'
            sleep 5
        }

    }


    stage('manual-approval') {
        input 'manual-approval ?'
    }

    stage('deploy') {
        node("build") {
            echo 'deploys'
            sleep 5
        }

    }




}