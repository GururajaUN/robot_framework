pipeline {
    agent any
    stages {
        stage('robot test') {
            steps {
                sh '''
                docker run --shm-size=1g -e BROWSER=chrome -v /Users/gururajaun/.jenkins/workspace/pipelinetest:/opt/robotframework/tests:Z -v /Users/gururajaun/.jenkins/workspace/pipelinetest/robot-reports:/opt/robotframework/reports:Z ppodgorsek/robot-framework:latest
                '''
            }
        }
    }
}
