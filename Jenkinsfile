pipeline {
    agent none
    stages {
        stage('robot test') {
            agent { docker {
                image 'ppodgorsek/robot-framework:latest'
                       
                args '--shm-size=2g -v /Users/gururajaun/jenkins/robot_framework:/var/log/chromedriver:Z' }
            }

            options { skipDefaultCheckout() }

            environment {
                BROWSER = 'chrome'
            }
            steps {
                sh '''
                export ROBOT_TESTS_DIR=$WORKSPACE
                export ROBOT_REPORTS_DIR=$WORKSPACE/robot-reports
                /opt/robotframework/bin/run-tests-in-virtual-screen.sh --shm-size=1g
                '''
            }
        }
    }
}

