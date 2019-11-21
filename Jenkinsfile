pipeline {
  agent any
  stages {
    stage('Terminate Instance') {
      steps {
        sh '''aws ec2 terminate-instances --region us-east-1 --instance-ids $(aws ec2 describe-instances --region us-east-1 --query \'Reservations[].Instances[].InstanceId\' --filters "Name=tag:name,Values= Webserver" --output text)
'''
      }
    }

    stage('Wait to Terminate Instance') {
      steps {
        sleep 60
      }
    }

    stage('Create Instance') {
      steps {
        sh 'aws ec2 run-instances --region us-east-1 --launch-template LaunchTemplateId=lt-02e4b99fe1eecdcf6,Version=3'
      }
    }

    stage('Wait for Instance Creation') {
      steps {
        sleep 60
      }
    }

    stage('Send Email') {
      steps {
        emailext(subject: 'Instance Launched', body: 'The instance has been launched', attachLog: true, from: 'jnraajan@gmail.com', to: 'jnraajan@gmail.com')
      }
    }

  }
}