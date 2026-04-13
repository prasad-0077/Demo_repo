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
              docker --version
              '''
    }
}
        stage('Build Docker Image') {
           steps {
           sh '''
           export PATH=/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
           docker build -t myapp:latest .
           '''
    }
}

        stage('Run Docker Container') {
            steps {
                script {
                sh '''
                export PATH=/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin

                echo "Running Docker container..."

                docker rm -f myapp-container || true
                docker run -d --name myapp-container -p 3000:3000 myapp:latest
                '''
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
