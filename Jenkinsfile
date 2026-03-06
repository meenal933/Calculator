pipeline {
    agent any

    environment {
        PATH = "/opt/homebrew/bin:/usr/local/bin:/usr/bin:/bin"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/meenal933/Calculator'
            }
        }

        stage('Install Dependencies') {
    steps {
        sh 'pip3 install --break-system-packages fastapi uvicorn pytest'
    }
}

        stage('Run Tests') {
            steps {
                sh 'pytest test.py'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t meenal933/calculator .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push meenal933/calculator'
            }
        }

        stage('Deploy') {
            steps {
                sh 'ansible-playbook -i inventory deploy.yml'
            }
        }
    }
}