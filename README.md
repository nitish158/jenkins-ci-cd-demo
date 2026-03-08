pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/YOUR_USERNAME/jenkins-ci-cd-demo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-demo .'
            }
        }

    }
}
