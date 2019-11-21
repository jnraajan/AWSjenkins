pipeline {
  agent any
  stages {
    stage('Launch Instance') {
      steps {
        sh 'aws ec2 run-instances --launch-template LaunchTemplateId=lt-02e4b99fe1eecdcf6,Version=3, Region=us-east-1b'
      }
    }

  }
}