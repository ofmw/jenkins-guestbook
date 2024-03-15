pipeline {
    agent any

    enviroment {
        APPROVAL_NO = ''
    }

    stages {
        stage('Checkout') { steps { echo "Checkout" } }
        stage('Build') { steps { echo "Build" } }
        stage('Docker Image Build') { steps { echo "Docker Image Build" } }
        stage('Docker Image Push') { steps { echo "Docker Image Push" } }
        stage('Staging Deploy') { steps { echo "Staging Deploy" } }
    }

    post {
        success {
            slackSend(tokenCredentialId: 'slack-token',
            channel: '#빌드-배포',
            color: 'good',
            message: "${JOB_NAME} (${BUILD_NUMBER}) 빌드 성공 (<${BUILD_URL}>)")
        }
        failure {
            slackSend(tokenCredentialId: 'slack-token',
            channel: '#빌드-배포',
            color: 'danger',
            message: "${JOB_NAME} (${BUILD_NUMBER}) 빌드 실패 (<${BUILD_URL}>)")
        }
    }
}
