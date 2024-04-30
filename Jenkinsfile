@Library(['github.com/indigo-dc/jenkins-pipeline-library@release/2.1.1']) _

def projectConfig

pipeline {
    agent any

    stages {
        stage('Application testing') {
            // do not execute Application Testing, if Dockerfile.cicd has changed
            when {
                not {
                    changeset 'Dockerfile.cicd'
                }
            }
            steps {
                script {
                    projectConfig = pipelineConfig()
                    buildStages(projectConfig)
                }
            }
        }
    }
    post {
        // publish results and clean-up
        always {
            // Clean after build
            cleanWs()
        }
    }
}

