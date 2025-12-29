pipeline {
    agent any
    
    tools {
        maven 'Maven'  // Maven tool configured in Jenkins
    }
    
    environment {
        // variables defined here can be used by any stage
        NEW_VERSION = '1.3.0'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[
                        url: 'https://github.com/mightykarim/static1.git',
                        credentialsId: 'github-token'
                    ]]
                ])
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building Project'
                echo "Building version ${NEW_VERSION}"
                
                // Use Maven commands instead of nvm
                sh 'mvn --version'  // Check Maven is installed
                sh 'mvn clean compile'  // Example Maven build command
                
                // If you need Node.js for your project, install it directly:
                sh '''
                    # Install Node.js directly (alternative to nvm)
                    curl -fsSL https://deb.nodesource.com/setup_18.x | bash -
                    apt-get install -y nodejs
                    node --version
                    npm --version
                '''
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'mvn test'  // Example Maven test command
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'echo "Deployment would happen here"'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed!'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
