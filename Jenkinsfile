pipeline {
  agent any
  environment {
        AWS_ACCESS_KEY_ID     = credentials('aws-jenkins-cr')
        AWS_SECRET_ACCESS_KEY = credentials('aws-jenkins-cr')
       // AWS_DEFAULT_REGION_US_EAST_1 = 'us-east-1'
       // AWS_DEFAULT_REGION_AP_SOUTH_1 = 'ap-south-1'
       // AWS_DEFAULT_REGION_EU_WEST_1 = 'eu-west-2'
    }

   stages {

    stage('Checkout code') {
      steps {
        git branch: 'main', url: 'https://github.com/psivaramps/webapplication-tg-alb.git'
      }
    }
     
    stage('Terraform Init') {
      steps {
        
        sh 'terraform init'
      }
    }
     
  stage('Terraform Plan') {
      steps {
        
        sh 'terraform plan'
      }

    }
     
    stage('Terraform Apply') {
      steps {
        //input 'Apply the changes?'
        sh 'terraform apply -auto-approve'
      }
    }
  }
}
