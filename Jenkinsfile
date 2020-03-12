pipeline {
    agent none
    stages {
        stage('robot test') {
            agent { docker {
                image 'ypasmk/robot-framework:latest' 
                args '--shm-size=1g -v $WORKSPACE/output:/output -v $WORKSPACE/robot-tests:/suites -v $WORKSPACE/scripts:/scripts -v $WORKSPACE/robot-reports:/reports --security-opt seccomp:unconfined' }
            }

            options { skipDefaultCheckout() }

            environment {
                BROWSER = 'chrome'
                USERNAME = 'Gururaja'
            }
            steps {
                sh '''
                df -h
                echo $PATH
                printenv
                '''
            }
        }
    }
}
