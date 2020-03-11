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
                export ROBOT_TESTS_DIR=/Users/gururajaun/jenkins/robot_framework/robot-tests
                export ROBOT_REPORTS_DIR=/Users/gururajaun/jenkins/robot_framework/robot-reports
                /opt/robotframework/bin/run-tests-in-virtual-screen.sh
                '''
            }
        }
    }
}
