pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh '''
                    python3 -m venv .venv
                    .venv/bin/pip install --upgrade pip
                    .venv/bin/pip install -r requirements.txt
                '''
            }
        }

        stage('Unit Test') {
            steps {
                sh '''
                    .venv/bin/pytest
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    zip -r hello-devops.zip app.py test_app.py requirements.txt
                '''
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

