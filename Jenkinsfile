pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        // Here you can define commands for your build
        }
      }
    stage('Test') {
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
      //The conditions here will execute after the build is done
    always{
       // this action will always happen 
      echo 'post build condition Running'
          }
    failure {
      //only if failed
      echo 'post action if build failed'
          }
      }
}
