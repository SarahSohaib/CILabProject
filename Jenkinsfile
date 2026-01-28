pipeline {
    agent any

    stages {

        stage('Build') {
            when {
                branch 'main'
            }
            steps {
                echo 'Running full CI pipeline on main branch'
                bat 'mvn clean test'
            }
        }

        stage('Feature Branch Tests') {
            when {
                expression { env.BRANCH_NAME.startsWith('feature/') }
            }
            steps {
                echo 'Running tests only for feature branch'
                bat 'mvn test'
            }
        }

        stage('Release Validation') {
            when {
                expression { env.BRANCH_NAME.startsWith('release/') }
            }
            steps {
                echo 'Running tests and security checks for release branch'
                bat 'mvn test'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
