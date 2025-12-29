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
        stage('Build') {
            steps {
                echo 'Building Project'
                // using environment variable
                // To output the value of variable in string use " "
                echo "Building version ${NEW_VERSION}"
                bat "nvm install"
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
}
