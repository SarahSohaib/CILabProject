pipeline {
    agent any

    stages {

        stage('Build') {
            when {
                branch 'main'
            }
            steps {
                echo "Running full build on MAIN branch"
                bat '"C:\\Users\\Sarah Sohaib\\Downloads\\setups\\apache-maven-3.9.12-bin\\apache-maven-3.9.12\\bin\\mvn.cmd" clean compile'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests"
                bat '"C:\\Users\\Sarah Sohaib\\Downloads\\setups\\apache-maven-3.9.12-bin\\apache-maven-3.9.12\\bin\\mvn.cmd" test'
            }
        }

        stage('Security Scan (Release only)') {
            when {
                expression {
                    env.BRANCH_NAME.startsWith("release/")
                }
            }
            steps {
                echo "Running security checks for RELEASE branch"
                echo "Simulated security scan completed"
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully for ${env.BRANCH_NAME}"
        }
        failure {
            echo "Pipeline failed for ${env.BRANCH_NAME}"
        }
    }
}
