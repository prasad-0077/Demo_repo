pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/<prasad-0077>/Jenkins.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
    }
}
