pipeline {
    agent any
    environment{
      ECR_CREDENTIALS = credentials('iam')
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t kmigap/webapp-aws .'
            }
        }
        stage('Login') {
            steps {
                sh 'echo $ECR_CREDENTIALS_PSW | docker login -u $ECR_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push') {
            steps {
                sh 'docker push kmigap/webapp-aws'
            }
        }
        stage('Logout') {
            steps {
                sh 'docker logout'
            }
        }
    }
}
