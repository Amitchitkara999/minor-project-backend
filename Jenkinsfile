pipeline {
    agent any

    environment {
        NODE_ENV = 'development'
    }

    tools {
        nodejs 'node'
    }

    triggers {
        pollSCM('H/5 * * * *')
    }

    stages {

        stage('Repository Checking') {
            steps {
                echo 'Cloning the Git repository'
                git branch: 'main',
                    url: 'https://github.com/KaranManhas22/backend.git'
            }
        }

        stage('Install Node.js Dependencies') {
            steps {
                echo 'Installing Node.js dependencies'
                sh 'npm install'
            }
        }

        stage('Run') {
            steps {
                echo 'Running application'
                sh 'npm start'
            }
        }
    }

    post {
        success {
            echo 'Compiled successfully'
        }

        failure {
            echo 'Not compiled'
        }
    }
}