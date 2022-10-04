pipeline {
    agent any

    stages {
        stage('Install'){
            steps {
                echo "Installing packages..."
                sh "yarn install"
            }
        }
        stage('Test') {
            steps {
                echo "Test"

            }
        }

        stage('Build and Export') {
            steps {
                sh "yarn export"
            }
        }
        stage('deploy') {
            steps {
              sh "aws configure set region $AWS_DEFAULT_REGION" 
              sh "aws configure set aws_access_key_id $AWS_ACCESS_KEY_ID"  
              sh "aws configure set aws_secret_access_key $AWS_SECRET_ACCESS_KEY"
              sh "aws s3 sync /var/jenkins_home/workspace/frontend/out s3://sortlogfrontend"
            }
        }
    }
}
