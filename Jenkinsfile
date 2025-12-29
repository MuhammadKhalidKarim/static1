pipeline {
    agent any
    
    tools {
        maven 'Maven'  // This should match the Maven tool name configured in Jenkins
    }
    
    environment {
        // variables defined here can be used by any stage
        NEW_VERSION = '1.3.0'
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub with credentials
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[
                        url: 'https://github.com/mightykarim/static1.git',
                        credentialsId: 'github-token'  // Your GitHub credentials
                    ]]
                ])
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building Project'
                // using environment variable
                // To output the value of variable in string use " "
                echo "Building version ${NEW_VERSION}"
                sh "nvm install"
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing..'
                // Here you can define commands for your tests
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                // Here you can define commands for your deployment
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed!'
        }
    }
}
