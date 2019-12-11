pipeline {
  agent any
  stages {
    stage('Clean') {
      steps {
        sh 'echo Clean'
      }
    }

    stage('Build') {
      steps {
        sh 'echo Build'
        sleep 3
      }
    }

    stage('Checkstyle') {
      steps {
        sh 'echo Checkstyle'
      }
    }

    stage('Find bugs') {
      steps {
        sh 'echo Find bugs'
      }
    }

    stage('OWASP') {
      steps {
        sh 'echo OWASP'
      }
    }

    stage('Unit test') {
      steps {
        sleep 1
        sh 'echo Unit test'
      }
    }

    stage('Functional tests') {
      steps {
        sh 'echo Functional tests'
      }
    }

    stage('Deploy') {
      steps {
        withCredentials(bindings: [sshUserPrivateKey(credentialsId: 'SMNLLCEC2', \
                                                             keyFileVariable: 'SSH_KEY_FOR_EC2')]) {
          sh 'ls -lrt'
          sh 'scp -i $SSH_KEY_FOR_EC2 -oStrictHostKeyChecking=no index.html ec2-user@54.242.8.242:/var/www/html'
        }
      }
    }

    //stage('Send Email') {
      //steps {
      //  emailext(subject: 'Instance Launched', body: 'The instance has been launched', attachLog: true, from: 'jnraajan@gmail.com', to: 'jnraajan@gmail.com')
      //}
    //}
  }
}