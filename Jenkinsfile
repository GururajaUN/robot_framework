pipeline {
    agent none
    stages {
        stage('robot test') {
            steps {
                sh '''
                docker run --shm-size=1g -e BROWSER=chrome -v /Users/gururajaun/.jenkins/workspace/pipelinetest:/opt/robotframework/reports:Z -v /Users/gururajaun/.jenkins/workspace/pipelinetest/robot-reports:/opt/robotframework/tests:Z ppodgorsek/robot-framework:latest
                '''
            }
        }
    }
}
