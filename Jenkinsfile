pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/DevopsYaml/PythonApp/'
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
