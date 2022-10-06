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
              withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'awscredentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
    // some block}
               sh "aws configure set region $AWS_DEFAULT_REGION" 
               sh "aws s3 sync /var/jenkins_home/workspace/frontend/out s3://sortlogfrontend"
            }
        }
     }
   }
}
