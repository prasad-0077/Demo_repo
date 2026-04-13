pipeline {
    agent any

    environment {
        IMAGE_NAME = "myapp"
        IMAGE_TAG  = "latest"
    }

    stages {

        stage('Checkout Demo_repo') {
            steps {
                withCredentials([string(credentialsId: 'MY_PAT', variable: 'TOKEN')]) {
                    git url: "https://${TOKEN}@github.com/prasad-0077/Demo_repo.git", branch: 'main'
                }
            }
        }
        stage('Check Docker') {
           steps {
                sh '''
                export PATH=/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
                echo "PATH is: $PATH"
                sh which docker
                sh docker --version
                '''
    }
}
        stage('Build Docker Image') {
            steps {
                sh '''
                export PATH=/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
                docker build -t myapp:latest .
                '''
                script {
                    echo "Building Docker image..."
                    dockerImage = docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    echo "Running Docker container..."

                    // Stop old container if running
                    sh "docker rm -f myapp-container || true"

                    // Run new container
                    sh """
                        docker run -d --name myapp-container -p 3000:3000 ${IMAGE_NAME}:${IMAGE_TAG}
                    """
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

    post {
        always {
            echo "Pipeline completed!"
        }
    }
}
