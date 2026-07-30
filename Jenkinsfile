pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                echo 'Repository Cloned'
            }
        }

        stage('Setup Python') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                . venv/bin/activate
                pytest
                '''
            }
        }

        stage('Build') {
            steps {
                echo 'Build Successful'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                . venv/bin/activate
                nohup python app.py &
                '''
            }
        }
    }
}