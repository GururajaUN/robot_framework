pipeline {
    agent none
    stages {
        stage('robot test') {
            agent { docker {
                image 'ppodgorsek/robot-framework:3.2.2' 
                args '--shm-size=1g' }
            }

            options { skipDefaultCheckout() }

            environment {
                BROWSER = 'firefox'
            }
            steps {
                sh '''
                df -h
                echo $PATH
                printenv
                ls -al /opt/robotframework/bin/
                export ROBOT_TESTS_DIR=$WORKSPACE/robot-tests
                export ROBOT_REPORTS_DIR=$WORKSPACE/robot-reports
                echo $ROBOT_TESTS_DIR
                ls -al $ROBOT_TESTS_DIR
                ls -al /opt/robotframework/tests/
                /opt/robotframework/bin/run-tests-in-virtual-screen.sh || true
                ls -al /var/log/
                '''
            }
        }
    }
}
