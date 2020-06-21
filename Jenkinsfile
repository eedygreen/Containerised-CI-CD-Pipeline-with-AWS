pipeline {
    agent any
    stages {

        stage('Clone git repo') {
            steps {
                sh 'echo "STAGE 0: Cloning app code from SCM ..."'
                git 'https://github.com/eedygreen/Containerised-CI-CD-Pipeline-with-AWS.git'
            }
        }
            
        stage('Create kubernetes cluster') {
            steps {
                withAWS(region:'us-east-1', credentials:'aws-credentials') {
                    sh 'eksctl create cluster --name profile --version 1.16 --nodegroup-name standard-workers --node-type t2.micro --nodes 2 --nodes-min 1 --nodes-max 3 --node-ami auto --region us-east-1 --zones us-east-1a --zones us-east-1b --zones us-east-1c'
                }
            }
        }
      
    

        stage('Create conf file cluster') {
            steps {
                withAWS(region: 'us-east-1', credentials: 'aws-credentials') {
                sh 'aws eks --region us-east-1 update-kubeconfig --name profile'
                }

            }   
        }
    }   
}

