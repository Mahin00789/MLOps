
pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'file:///D:/College/MLOPS/Jenkins/Scenario-2'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'python -m pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'python -m pytest -v'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t flask-ci-cd-demo:latest .'
            }
        }

        stage('Deploy Container') {
            steps {
                bat 'docker rm -f flask-ci-cd-demo 2>NUL'
                bat 'docker run -d --name flask-ci-cd-demo -p 8000:8000 flask-ci-cd-demo:latest'
            }
        }
    }
}
