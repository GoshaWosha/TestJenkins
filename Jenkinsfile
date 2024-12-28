pipeline {
  agent any
  tools {
    maven "Maven" // Keep Maven if necessary for other builds; otherwise, you can remove it.
  }
  environment {
    NEW_VERSION = '1.3.0'
    VENV_DIR = 'venv' // Name of the virtual environment directory
  }
  stages {
    stage('Clone Repository') {
      steps {
        echo 'Cloning the Flask application repository...'
        git 'https://github.com/realpython/flask-boilerplate'
      }
    }
    stage('Set Up Environment') {
      steps {
        echo 'Setting up Python virtual environment...'
        sh """
          python3 -m venv ${VENV_DIR}
          source ${VENV_DIR}/bin/activate
          pip install --upgrade pip
          pip install -r requirements.txt
        """
      }
    }
    stage('Build') {
      steps {
        echo 'Building the Flask application...'
        echo "Building version ${NEW_VERSION}"
        sh """
          source ${VENV_DIR}/bin/activate
          python setup.py build
        """
      }
    }
    stage('Test') {
      when {
        expression {
          flag == true // Ensure `flag` controls whether tests are run
        }
      }
      steps {
        echo 'Running tests...'
        sh """
          source ${VENV_DIR}/bin/activate
          pytest
        """
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying the Flask application...'
        sh """
          source ${VENV_DIR}/bin/activate
          flask run --host=0.0.0.0 --port=5000 &
        """
      }
    }
  }
  post {
    always {
      echo 'Post-build actions running...'
    }
    failure {
      echo 'Build failed!'
    }
  }
}
