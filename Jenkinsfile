pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "D:\\Documents\\Deakin\\2024 Trimester 2\\SIT223\\6.1C\\Code"
        TESTING_ENVIRONMENT = "6.1C Testing Environment"
        PRODUCTION_ENVIRONMENT = "Daniel Soutar - Production Environment"
    }

    stages {
        stage("Build") {
            steps {
                echo "Fetch the source code from the directory path specified by the environment variable: $DIRECTORY_PATH"
                echo "Compile the code and generate any necessary artifacts"
            }
        }
        stage("Test") {
            steps {
                echo "Unit tests"
                echo "Integration tests"
            }
        }
        stage("Code Quality Check") {
            steps {
                echo "Check the quality of the code"
            }
        }
        stage("Deploy") {
            steps {
                echo "Deploy the application to a testing environment specified by the environment variable: $TESTING_ENVIRONMENT"
            }
        }
        stage("Approval") {
            steps {
                echo "Simulate manual approval with a 10 second sleep"
                sleep(time:10, unit:"SECONDS")
            }
        }
        stage("Deploy to Production") {
            steps {
                echo "Deploy the application to the production environment: $PRODUCTION_ENVIRONMENT"
            }
        }
    }
}
