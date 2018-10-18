pipeline {
    agent any
    stages {
        stage('Create sanboxes') {
            steps { 
                sh 'printenv'
                mkdir -p /var/www/sandbox/${env.CHANGE_BRANCH}
                //slackSend (color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
                ln -s ${env.WORKSPACE} /var/www/sandbox/${env.CHANGE_BRANCH}/${env.CHANGE_AUTHOR}
            }
        }
    }
    post {
            success {
                slackSend (color: '#00FF00', message: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
            }
            failure {
                slackSend (color: '#FF0000', message: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
            }
        }
}