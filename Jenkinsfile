pipeline {
    agent any

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
        stage('Test') {
            steps {
                echo 'Running dummy tests for Android application...'
                build(job: 'android-app-test-dummy')
            }
            post {
                failure {
                    echo 'Running dummy tests for Android application failed...'
                    mail body: "Dummy tests failed for ${env.JOB_NAME}", subject: "Dummy Tests Failed", to: "mystudies9633@gmail.com"
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying Android application...'
                build(job: 'android-app-deployement')
            }
            post {
                failure {
                    echo 'Deploying Android application failed...'
                    mail body: "Android deployment failed for ${env.JOB_NAME}", subject: "Android Deployment Failed", to: "mystudies9633@gmail.com"
                }
            }
        }
    }

    post {
        success {
            echo 'Android pipeline succeeded...'
            mail body: "Android pipeline succeeded for ${env.JOB_NAME}", subject: "Android Pipeline Succeeded", to: "mystudies9633@gmail.com"
        }
    }
}
