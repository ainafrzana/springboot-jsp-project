pipeline {
    agent any

    tools {
        maven 'Maven3' // Make sure this matches the name in Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                // Replace with your URL and Credentials ID from Jenkins
                git branch: 'main', url: 'https://github.com/ainafrzana/springboot-jsp-project.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean install' 
                // Use 'bat' instead of 'sh' if your Jenkins is running on Windows
            }
        }

        stage('Deploy') {
            steps {
                // This step requires the "Deploy to container" plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcat-admin', url: 'http://localhost:8080')], 
                       contextPath: 'springboot-jsp-app', 
                       war: 'target/*.war'
            }
        }
    }
}