pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m pip install -r requirements.txt'
            }
        }

        stage('Unit Test') {
            steps {
                sh 'python3 -m pytest'
            }
        }

        stage('Build') {
            steps {
                sh 'zip -r hello-devops.zip . -x ".git/*"'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'hello-devops.zip',
                                 fingerprint: true
            }
        }
    }
}
