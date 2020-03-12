pipeline {
    agent none
    stages {
        stage('robot test') {
            agent { docker {
                image 'ppodgorsek/robot-framework:latest' 
                args '--shm-size=1g' }
            }

            options { skipDefaultCheckout() }

            environment {
                BROWSER = 'chrome'
            }
            steps {
                sh '''
                df -h
                echo $PATH
                printenv
                echo $ROBOT_OPTIONS
                ls -al /opt/robotframework/bin/
                mv /opt/robotframework/bin /opt/robotframework/bin_1
                export ROBOT_TESTS_DIR=$WORKSPACE
                export ROBOT_REPORTS_DIR=$WORKSPACE/robot-reports
                /opt/robotframework/bin_1/run-tests-in-virtual-screen.sh || true
                cat /var/log/chromedriver
                '''
            }
        }
    }
}
