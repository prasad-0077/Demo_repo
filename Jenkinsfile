pipeline {
    agent any

    stages {

        stage('Checkout Demo_repo') {
            steps {
                git(
                    url: 'https://github.com/prasad-0077/Demo_repo.git',
                    credentialsId: 'MY_PAT',
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
                        credentialsId: 'MY_PAT'
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
