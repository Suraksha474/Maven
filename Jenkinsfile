pipeline {
    agent any
    tools {
        // Set the Maven version from the Global Tool Configuration in Jenkins
        maven 'Maven-3.9.9' // Replace with your Maven version name from Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                // Clone the GitHub repository
                git 'https://github.com/Suraksha474/Maven.git'
            }
        }
        stage('Build') {
            steps {
                // Run the Maven build
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                // Run the tests
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                // Package the application
                sh 'mvn package'
            }
        }
    }
    post {
        always {
            // Archive build artifacts
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
        }
        failure {
            // Send a notification when the build fails (optional)
            echo 'Build failed!'
        }
    }
}
