pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                bat 'python -m venv venv'
                bat 'call venv\\Scripts\\activate.bat && pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                bat 'call venv\\Scripts\\activate.bat && pytest -v --junitxml=results.xml'
            }
        }
    }

    post {
        always {
            junit 'results.xml'
        }
    }
}
