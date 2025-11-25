pipeline {
    agent any

    stages {

        stage('Checkout Demo_repo') {
            steps {
                withCredentials([string(credentialsId: 'MY_PAT', variable: 'TOKEN')]) {
                    git url: "https://${TOKEN}@github.com/prasad-0077/Demo_repo.git", branch: 'main'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo 'Building Docker image...'
                    dockerImage = docker.build("myapp:latest")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    echo 'Running Docker container...'
                    dockerImage.run("-p 3000:3000") // change ports if needed
                }
            }
        }

        stage('Build') {
            steps {
                echo 'Other build steps (if any)...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests (if any)...'
            }
        }

    }
}
