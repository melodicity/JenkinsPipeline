pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                echo "Building ..."
            }
            post {
                always {
                    mail to: "s223387609@deakin.edu.au"
                    subject: "Build Status Email"
                    body: "Build log attached!"
            }
        }
        stage("Test") {
            steps {
                echo "Testing..."
            }
        }
        stage("Deploy") {
            steps {
                echo "Deploying..."
            }
        }
    }
}
