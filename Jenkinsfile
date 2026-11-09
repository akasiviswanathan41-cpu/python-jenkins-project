pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/akasiviswanathan41-cpu/python-jenkins-project.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    python3 -m venv venv
                    ./venv/bin/pip install -r requirements.txt
                '''
            }
        }

        stage('Run Python Tests') {
            steps {
                sh './venv/bin/pytest -v'
            }
        }
    }

    post {
        success {
            echo 'Python tests completed successfully!'
        }

        failure {
            echo 'Python testing failed!'
        }
    }
}
