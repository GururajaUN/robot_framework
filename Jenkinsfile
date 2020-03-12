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
                echo $ROBOT_OPTIONS
                ls -al /opt/robotframework/bin/
                export ROBOT_TESTS_DIR=$WORKSPACE
                export ROBOT_REPORTS_DIR=$WORKSPACE/robot-reports
                /opt/robotframework/bin/run-tests-in-virtual-screen.sh || true
                ls -al /var/log/
                '''
            }
        }
    }
}
