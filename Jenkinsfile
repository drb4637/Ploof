pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building'
        sh 'echo password | sudo -S pip install pytest '
      }
    }
    stage('Test') {
      parallel {
        stage('error') {
          steps {
            echo 'Gonna try and run a test'
          }
        }
        stage('error') {
          steps {
            sh '''
pytest --verbose --junit-xml test.xml test.py'''
          }
        }
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying'
      }
    }
  }
  environment {
    PATH = '/opt/miniconda2/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin'
  }
  post {
    always {
	junit 'build/test.xml'
    }

    always {
      echo 'This will always run'

    }

    success {
      echo 'This will run only if successful'

    }

    failure {
      echo 'This will run only if failed'

    }

    unstable {
      echo 'This will run only if the run was marked as unstable'

    }

    changed {
      echo 'This will run only if the state of the Pipeline has changed'
      echo 'For example, if the Pipeline was previously failing but is now successful'

    }

  }
}
