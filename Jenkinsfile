pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building Android application...'
                build(job: 'android-app-build')
            }
            post {
                failure {
                    echo 'Building Android application failed...'
                    mail body: "Android build failed for ${env.JOB_NAME}", subject: "Android Build Failed", to: "mystudies9633@gmail.com"
                }
            }
        }
        stage('Deploy and Test') {
            steps {
                echo 'Running Deploy & Test for Android application...'
                build(job: 'android-app-test')                
            }
            post {
                failure {
                    echo 'Running Deploy & Test for Android application failed...'
                    mail body: "Deploy & Test failed for ${env.JOB_NAME}", subject: "Deploy & Test Failed", to: "mystudies9633@gmail.com"
                }
            }
        }
        stage('Release') {
            steps {
                echo 'Release Android application...'
                build(job: 'android-app-deployement')
            }
            post {
                failure {
                    echo 'Replease Android application failed...'
                    mail body: "Android app release failed for ${env.JOB_NAME}", subject: "Android app release failed", to: "mystudies9633@gmail.com"
                }
            }
        }        
    }

    post {
        success {
            echo 'Android pipeline succeeded...'
            slackSend channel: 'android-ci-cd-updates', message: "Android pipeline run completed for ${env.JOB_NAME} ${env.BUILD_NUMBER} ${env.BUILD_URL} with a ${currentBuild.currentResult} status"
            mail body: "Android pipeline succeeded for ${env.JOB_NAME}", subject: "Android Pipeline Succeeded", to: "mystudies9633@gmail.com"
        }
    }
}
