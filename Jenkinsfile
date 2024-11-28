flag = true
pipeline {
  agent any
    tools {
      maven "Maven"
    }
  environment {
      NEW_VERSION = '1.3.0'
  }
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        // Here you can define commands for your build
        echo "Building version ${NEW_VERSION}"
        sh "npm install -g n"
      }
    }
    stage('Test') {
      when {
        expression {
          flag == false
        }
      }
      steps {
        echo 'Testing..'
        // Here you can define commands for your tests
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
        // Here you can define commands for your deployment
      }
    }
  }
  post {
    always {
      // this action will always happen
      echo 'post build condition Running'
    }
    failure {
      // only if failed
      echo 'post action if build failed'
    }
  }
}
