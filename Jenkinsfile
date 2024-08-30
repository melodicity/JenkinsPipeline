pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                echo "Building and packaging with Maven"
                echo "mvn package"
                // Maven command to compile, build and package the source code
            }
        }
        stage("Unit and Integration Tests") {
            steps {
                echo "Testing with Maven"
                echo "mvn test"
                // Maven command to run both Unit and Integration Testing
            }
            post {
                success {
                    emailext to: "dsoutar812@gmail.com",
                    subject: "Unit and Integration Tests Passed",
                    body: "Build log attached.",
                    attachLog: true
                }
                failure {
                    emailext to: "dsoutar812@gmail.com",
                    subject: "Unit and Integration Tests Failed",
                    body: "Build log attached.",
                    attachLog: true
                }
            }
        }
        stage("Analysis") {
            steps {
                echo "Analysing code with SonarQube"
                echo "sonar-scanner"
                // SonarQube command to perform code analysis
            }
        }
        stage("Security Scan") {
            steps {
                echo "Running security scan with OWASP ZAP"
                echo "zap-cli start"
                echo "zap-cli open-url http://localhost:8080"
                echo "zap-cli active-scan http://localhost:8080"
                echo "zap-cli report -o zap_report.html -f html"
                // ZAP commands to perform a security scan
            }
            post {
                success {
                    emailext to: "dsoutar812@gmail.com",
                    subject: "Security Scan Passed",
                    body: "Build log attached.",
                    attachLog: true
                }
                failure {
                    emailext to: "dsoutar812@gmail.com",
                    subject: "Security Scan Failed",
                    body: "Build log attached.",
                    attachLog: true
                }
            }
        }
        stage("Deploy to Staging") {
            steps {
                echo "Deploying to an AWS EC2 staging environment"
                echo "aws s3 cp target/app.war s3://my-staging-bucket/app.war"
                echo "aws ec2 describe-instances --filters 'Name=tag:Name,Values=StagingServer'"
                echo "aws ec2 start-instances --instance-ids i-0123456789abcdef0"
                // AWS commands to deploy the application to staging
            }
        }
        stage("Integration Testing on Staging") {
            steps {
                echo "Integration testing with Maven"
                echo "mvn failsafe:integration-test failsafe:verify"
                // Maven command to run integration testing
            }
            post {
                success {
                    emailext to: "dsoutar812@gmail.com",
                    subject: "Integration Tests on Staging Passed",
                    body: "Build log attached.",
                    attachLog: true
                }
                failure {
                    emailext to: "dsoutar812@gmail.com",
                    subject: "Integration Tests on Staging Failed",
                    body: "Build log attached.",
                    attachLog: true
                }
            }
        }
        stage("Deploy to Production") {
            steps {
                echo "Deploying to AWS EC2 production environment"
                echo "aws s3 cp target/app.war s3://my-production-bucket/app.war"
                echo "aws ec2 describe-instances --filters 'Name=tag:Name,Values=ProductionServer'"
                echo "aws ec2 start-instances --instance-ids i-0abcdef1234567890"
                // AWS commands to deploy the application to production
            }
        }
    }
}
