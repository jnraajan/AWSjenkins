pipeline {
  agent any
  stages {
    stage('Launch Instance') {
      steps {
        sh '''aws ec2 terminate-instances --region us-east-1 --instance-ids $(aws ec2 describe-instances --region us-east-1 --query \'Reservations[].Instances[].InstanceId\' --filters "Name=tag:name,Values= Webserver" --output text)
aws ec2 run-instances --region us-east-1 --launch-template LaunchTemplateId=lt-02e4b99fe1eecdcf6,Version=3'''
      }
    }

  }
}