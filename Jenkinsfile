pipeline {
    agent any

    triggers {
        pollSCM('H/2 * * * *')
    }

    stages {
        stage('Build') {
            steps {
                bat 'python --version'
                bat 'python -m py_compile app.py test_app.py'
                bat 'echo Build stage completed'
            }
        }

        stage('Test') {
            steps {
                bat 'python -m unittest -v'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed. Check the stage logs.'
        }
        always {
            echo 'Pipeline execution finished.'
        }
    }
}