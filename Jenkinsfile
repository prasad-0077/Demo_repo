pipeline {
    agent any

    stages {

        stage('Checkout Demo_repo') {
            steps {
                git(
                    url: 'https://github.com/prasad-0077/Demo_repo.git',
                    credentialsId: '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',
                    branch: 'main'
                )
            }
        }

        stage('Checkout Jenkins repo') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: 'main']],
                    doGenerateSubmoduleConfigurations: false,
                    extensions: [],
                    userRemoteConfigs: [[
                        url: 'https://github.com/prasad-0077/Jenkins.git',
                        credentialsId: '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'
                    ]]
                ])
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }

    }
}
