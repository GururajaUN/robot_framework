pipeline {
    agent none
    stages {
        stage('robot test') {
            agent { docker {
                image 'ppodgorsek/robot-framework:latest'
                       
                args '--shm-size=1g -u root' }
            }

            options { skipDefaultCheckout() }

            environment {
                BROWSER = 'firefox'
            }
            steps {
                sh '''
                export ROBOT_TESTS_DIR=$WORKSPACE
                export ROBOT_REPORTS_DIR=$WORKSPACE/robot-reports
                /opt/robotframework/bin/run-tests-in-virtual-screen.sh
                '''
            }
        }
    }
}