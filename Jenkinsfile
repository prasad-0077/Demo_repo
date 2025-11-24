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
                    credentialsId: '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', // replace with your Jenkins credential ID
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
                        credentialsId: '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' // same PAT credential
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
