

pipeline {
    agent any

    triggers {
        pollSCM('H/2 * * * *')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Starting Build Stage'

                bat '"C:/Users/GAGAN HS/AppData/Local/Programs/Python/Python310/python.exe" --version'

                bat '"C:/Users/GAGAN HS/AppData/Local/Programs/Python/Python310/python.exe" -m py_compile app.py test_app.py'

                bat '"C:/Users/GAGAN HS/AppData/Local/Programs/Python/Python310/python.exe" app.py'

                echo 'Build stage completed'
            }
        }

        stage('Test') {
            steps {
                echo 'Starting Test Stage'

                bat '"C:/Users/GAGAN HS/AppData/Local/Programs/Python/Python310/python.exe" -m unittest -v test_app'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }

        failure {
            echo 'Pipeline failed. Check the stage logs above.'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
