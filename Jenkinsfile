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
                sh "yarn prettier && yarn lint && yarn typecheck && yarn test"

            }
        }

        stage('Build and Export') {
            steps {
                sh "yarn build && yarn export"
            }
        }
        stage('deploy') {
            steps {
              sh "aws configure set region $AWS_DEFAULT_REGION" 
              sh "aws configure set aws_access_key_id $AWS_ACCESS_KEY_ID"  
              sh "aws configure set aws_secret_access_key $AWS_SECRET_ACCESS_KEY"
              sh "aws s3 cp ./index.html s3://sortlogfrontend"
            }
        }
    }
}