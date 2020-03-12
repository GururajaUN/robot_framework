pipeline {
    agent none
    stages {
        stage('robot test') {
            agent { docker {
                image 'ppodgorsek/robot-framework:3.2.2' 
                args '--shm-size=1g -v $WORKSPACE:/opt/robotframework/tests:Z -v $WORKSPACE/robot-reports:/opt/robotframework//opt/robotframework/reports:Z' }
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
                ls -al /opt/robotframework/tests/
                /opt/robotframework/bin/run-tests-in-virtual-screen.sh || true
                ls -al /var/log/
                '''
            }
        }
    }
}
