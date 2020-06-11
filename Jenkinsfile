pipeline {
  agent any
  stages {
    stage('Create Cluster') {
      steps {
        sh '''eksctl create cluster \\
                        --name profile \\
                        --version 1.13 \\
                        --nodegroup-name standard-workers \\
                        --node-type t2.micro \\
                        --nodes 2 \\
                        --nodes-min 1 \\
                        --nodes-max 3 \\
                        --node-ami auto \\
                        --region us-east-1 \\
                        --zones us-east-1a \\
                        --zones us-east-1b \\
                        --zones us-east-1c '''
      }
    }

  }
}