pipeline {
  agent any
  stages {
    stage('Build') {
      environment {
        PATH = '$PATH:/opt/miniconda2/bin'
      }
      steps {
        echo 'Building'
        sh 'ls'
        sh 'conda'
      }
    }
    stage('Test') {
      environment {
        PATH = '$PATH:/opt/miniconda2/bin'
      }
      parallel {
        stage('Test') {
          steps {
            echo 'Testing'
          }
        }
        stage('error') {
          steps {
            echo 'Gonna try and run a test'
          }
        }
        stage('error') {
          steps {
            sh '''pytest test.py
'''
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
  post {
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