pipeline {
    agent any
    
    tools {
        maven 'Maven'  // This is working!
    }
    
    environment {
        NEW_VERSION = '1.3.0'
    }
    
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/mightykarim/static1.git', branch: 'main'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building Project'
                echo "Building version ${NEW_VERSION}"
                
                // Maven commands - THESE WORK!
                sh 'mvn --version'
                sh 'mvn clean compile'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing..'
                // Optional: sh 'mvn test'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'echo "Deployment complete"'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed!'
        }
        success {
            echo '✅ Build succeeded!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
