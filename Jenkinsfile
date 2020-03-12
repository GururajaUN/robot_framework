pipeline {
    agent none
    stages {
        stage('robot test') {
            agent { docker {
                image 'ppodgorsek/robot-framework:latest'
                       
                args '--shm-size=1g -v /Users/gururajaun/.jenkins/workspace/pipelinetest:/opt/robotframework/tests -v /Users/gururajaun/.jenkins/workspace/pipelinetest/robot-report:/opt/robotframework/reports:Z' }
            }

            options { skipDefaultCheckout() }

            environment {
                BROWSER = 'chrome'
            }
            steps {
                sh '''
                ls -al /opt/robotframework/tests
                /opt/robotframework/bin/run-tests-in-virtual-screen.sh
                '''
            }
        }
    }
}

