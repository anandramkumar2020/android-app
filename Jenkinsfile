pipeline {
    agent any

    stages {
        stage('android-app-build') {
            steps {
                echo 'Building Android application...'
                build(job: 'android-app-build')
            }
            post {
                failure {
                    echo 'Building Android application failed...'
                    mail body: "Android build failed for ${env.JOB_NAME}", subject: "Android Build Failed", to: "anand.ramkumar@experionglobal.com"
                }
            }
        }
        stage('android-app-test-dummy') {
            steps {
                echo 'Running dummy tests for Android application...'
                build(job: 'android-app-test-dummy')
            }
            post {
                failure {
                    echo 'Running dummy tests for Android application failed...'
                    mail body: "Dummy tests failed for ${env.JOB_NAME}", subject: "Dummy Tests Failed", to: "anand.ramkumar@experionglobal.com"
                }
            }
        }
        stage('android-app-deployment') {
            steps {
                echo 'Deploying Android application...'
                build(job: 'android-app-deployement')
            }
            post {
                failure {
                    echo 'Deploying Android application failed...'
                    mail body: "Android deployment failed for ${env.JOB_NAME}", subject: "Android Deployment Failed", to: "anand.ramkumar@experionglobal.com"
                }
            }
        }
    }

    post {
        success {
            echo 'Android pipeline succeeded...'
            mail body: "Android pipeline succeeded for ${env.JOB_NAME}", subject: "Android Pipeline Succeeded", to: "anand.ramkumar@experionglobal.com"
        }
    }
}
