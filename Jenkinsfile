pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Restore') {
            steps {
                bat 'dotnet restore Homies.sln'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build Homies.sln --configuration Release --no-restore'
            }
        }

        stage('Test') {
            steps {
                bat 'dotnet test Homies.sln --configuration Release --no-build'
            }
        }
    }

    post {
        success {
            echo 'Build and tests passed.'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}
