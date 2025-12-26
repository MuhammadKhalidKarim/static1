pipeline {
    agent any

    environment {
        APP_VERSION = "1.0"
    }

    tools {
        maven 'Maven3' // Ensure Maven3 is configured in Jenkins → Manage Jenkins → Tools
    }

    parameters {
        booleanParam(name: 'executeTests', defaultValue: true)
    }

    stages {
        stage('Build') {
            steps {
                echo "Building App version ${APP_VERSION}..."
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            when {
                expression { params.executeTests }
            }
            steps {
                echo 'Running Tests...'
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying App...'
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
