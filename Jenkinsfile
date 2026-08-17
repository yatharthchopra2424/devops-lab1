pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'python3 --version'
                sh 'python3 -m py_compile app.py'
                echo 'Build stage complete'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh 'python3 -m unittest test_app.py -v'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh 'mkdir -p /tmp/deploy && cp app.py /tmp/deploy/'
                sh 'python3 /tmp/deploy/app.py'
                echo 'Deployed successfully'
            }
        }
    }

    post {
        success { echo 'Pipeline completed successfully' }
        failure { echo 'Pipeline failed' }
    }
}
