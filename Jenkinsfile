pipeline {

    agent any

    environment {
        AWS_DEFAULT_REGION = 'us-east-2'
        STACK_NAME = 'demo-ec2-stack'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/Shyamsandeep28/cloudformation-jenkins-lab.git'
            }
        }

        stage('Validate CloudFormation Template') {
            steps {

                sh '''
                aws cloudformation validate-template \
                --template-body file://ec2.yaml
                '''
            }
        }

        stage('Deploy CloudFormation Stack') {
            steps {

                sh '''
                aws cloudformation deploy \
                --template-file ec2.yaml \
                --stack-name $STACK_NAME
                '''
            }
        }

    }
}
