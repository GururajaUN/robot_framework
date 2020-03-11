pipeline {
    agent none
    stages {
        stage('robot test') {
            agent { docker {
                image 'ppodgorsek/docker-framework:latest'}
                args '--shm-size=1g'
            }

            options { skipDefaultCheckout() }

            environment {
                BROWSER = 'chrome'
            }
            steps {
                sh '''
                export ROBOT_TESTS_DIR=$WORKSPACE/robots-tests
                export ROBOT_REPORTS_DIR=$WORKSPACE/robots-reports
                /opt/robotframework/bin/run-tests-in-virtual-screen.sh
                '''
            }
        }
    }
}
