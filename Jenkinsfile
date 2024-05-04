pipeline {
    agent any

    stages {
        stage('android-app-build') {
            steps {
                echo 'Building Android application...'
                // Add commands to build the Android application
            }
            post {
                failure {
                    echo 'Building Android application failed...'
                    //mail body: "Android build failed for ${env.JOB_NAME}", subject: "Android Build Failed", to: "your-email@example.com"
                }
            }
        }
        stage('android-app-test-dummy') {
            steps {
                echo 'Running dummy tests for Android application...'
                // Add commands to run dummy tests
            }
            post {
                failure {
                    echo 'Running dummy tests for Android application failed...'
                    //mail body: "Dummy tests failed for ${env.JOB_NAME}", subject: "Dummy Tests Failed", to: "your-email@example.com"
                }
            }
        }
        stage('android-app-deployment') {
            steps {
                echo 'Deploying Android application...'
                // Add commands to deploy the Android application
            }
            post {
                failure {
                    echo 'Deploying Android application failed...'
                    //mail body: "Android deployment failed for ${env.JOB_NAME}", subject: "Android Deployment Failed", to: "your-email@example.com"
                }
            }
        }
    }

    post {
        success {
            echo 'Android pipeline succeeded...'
            mail body: "Android pipeline succeeded for ${env.JOB_NAME}", subject: "Android Pipeline Succeeded", to: "anandramkumar31@gmail.com"
        }
    }
}
