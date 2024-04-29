pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Delay') {
            steps {
                script {
                    // Sleep for 1 minute (60 seconds)
                    sleep(time: 60, unit: 'SECONDS')
                }
            }
        }
        stage('Build') {
            steps {
                // Your build steps here
            }
        }
    }
}
