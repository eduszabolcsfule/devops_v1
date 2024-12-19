pipeline {
    agent {
        docker {
            image 'python:3.9-slim'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                sh 'pytest' // Ha vannak tesztjeid
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t streamlit-app .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 8501:8501 --name streamlit-app streamlit-app'
            }
        }
    }
}
