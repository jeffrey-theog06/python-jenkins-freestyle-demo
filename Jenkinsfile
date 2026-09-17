pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                bat 'py.exe -m venv venv'
                bat 'call venv\\Scripts\\activate.bat && pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                bat 'call venv\\Scripts\\activate.bat && pytest -v --junitxml=results.xml'
            }
        }
        stage('Echo'){
            steps {
                echo "Hello World"
            }
        }
    }

    post {
        always {
            junit 'results.xml'
        }
    }
}
