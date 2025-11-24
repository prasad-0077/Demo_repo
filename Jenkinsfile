pipeline {
    agent any

    environment {
        // Optional: set environment variables if needed
    }

    stages {

        stage('Checkout Demo_repo') {
            steps {
                // Checkout first repository with credentials
                git(
                    url: 'https://github.com/prasad-0077/Demo_repo.git',
                    credentialsId: 'github-pat', // replace with your Jenkins credential ID
                    branch: 'main'
                )
            }
        }

        stage('Checkout Jenkins repo') {
            steps {
                // Checkout second repository with credentials
                checkout([$class: 'GitSCM',
                    branches: [[name: 'main']],
                    doGenerateSubmoduleConfigurations: false,
                    extensions: [],
                    userRemoteConfigs: [[
                        url: 'https://github.com/prasad-0077/Jenkins.git',
                        credentialsId: 'github-pat' // same PAT credential
                    ]]
                ])
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
                // Your build steps here
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                // Your test steps here
            }
        }

    }
}
