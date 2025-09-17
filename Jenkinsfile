pipeline {
    agent any

    stages {
        stage('Install Python in Jenkins Container') {
            steps {
                sh '''
                if ! command -v python3 >/dev/null 2>&1; then
                    echo "Installing Python..."
                    apt-get update
                    apt-get install -y python3 python3-pip python3-venv
                else
                    echo "Python already installed."
                fi
                '''
            }
        }

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/DevopsYaml/PythonApp/'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt || true
                '''
            }
        }

        stage('Run App') {
            steps {
                sh '''
                . venv/bin/activate
                python3 app.py
                '''
            }
        }
    }
}
