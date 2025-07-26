pipeline {
    agent any

    environment {
        VENV_DIR = 'venv'
        PYTHON = 'venv\\Scripts\\python.exe'
        PIP = 'venv\\Scripts\\pip.exe'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/SopheakkdeyChea/djangojenkins.git'
            }
        }

        stage('Setup Virtual Environment') {
            steps {
                bat 'python -m venv venv'
                bat '%PIP% install --upgrade pip'
                bat '%PIP% install -r requirements.txt'
            }
        }

        stage('Run Migrations') {
            steps {
                bat '%PYTHON% manage.py migrate'
            }
        }

        stage('Run Tests') {
            steps {
                bat '%PYTHON% manage.py test'
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying to production...'
                // Add deployment commands here
            }
        }
    }
}
