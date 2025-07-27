pipeline {
    agent any

    environment {
        PYTHON_HOME = 'C:\\Users\\LENOVO\\AppData\\Local\\Programs\\Python\\Python311'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Setup Virtual Environment') {
            steps {
                bat '"%PYTHON_HOME%\\python.exe" -m venv venv'
            }
        }

        stage('Activate Virtual Environment and Install Requirements') {
            steps {
                bat '.\\venv\\Scripts\\activate && pip install -r requirements.txt'
            }
        }

        stage('Run Migrations') {
            steps {
                bat '.\\venv\\Scripts\\activate && python manage.py migrate'
            }
        }

        stage('Run Tests') {
            steps {
                bat '.\\venv\\Scripts\\activate && python manage.py test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying your application...'
                // Add deployment steps here
            }
        }
    }
}
