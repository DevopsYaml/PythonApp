pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/DevopsYaml/PythonApp/'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                pip3 install --upgrade pip
                pip3 install -r requirements.txt || true
                '''
            }
        }

        stage('Run App') {
            steps {
                sh '''
                python3 app.py
                '''
            }
        }
    }
}
