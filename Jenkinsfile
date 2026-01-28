pipeline {
    agent any

    tools {
        maven 'Maven-3.9.12'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the project'
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
                bat 'mvn test'
            }
        }
    }

    post {
        success {
            echo 'Build and tests successful'
        }
        failure {
            echo 'Build or tests failed'
        }
    }
}
