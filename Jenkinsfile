pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: "https://github.com/meenal933/Calculator"
            }
        }
        stage('Test') {
            steps {
                sh 'pip install pytest httpx fastapi uvicorn'
                sh 'pytest test.py'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t meenal933/scientific_calculator .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]) {
                    sh 'echo $DOCKERHUB_PASSWORD | docker login -u $DOCKERHUB_USERNAME --password-stdin'
                    sh 'docker push meenal933/scientific_calculator'
                }
            }
        }
        stage('Deploy with Ansible') {
            steps {
                bat 'where wsl'
                bat 'wsl --cd /mnt/c/PHOTOS/Personal/Projects/SPE/MiniProject-main/Mini'
                bat 'wsl --exec ansible-playbook -i inventory deploy.yml'
            }
        }
    }
    post {
        always {
            script {
                def status = currentBuild.result ?: 'SUCCESS'
                mail to: 'meenalh007@gmail.com',
                     subject: "Jenkins Build: ${status}",
                     body: "The Jenkins pipeline execution has completed with status: ${status}.\n\nCheck the Jenkins console for more details: ${env.BUILD_URL}"
            }
        }
    }
}

