pipeline {
  agent any
  stages {
    stage('Launch Instance') {
      steps {
        sh 'aws ec2 run-instances --region us-east-1 --launch-template LaunchTemplateId=lt-02e4b99fe1eecdcf6,Version=3'
      }
    }

  }
}