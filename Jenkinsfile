pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/jcabezasp2/calculator2.git'
            }
        }
        // Normally I would set the permission in the dockerfile
        stage('Set Permissions') {
            steps {
                sh 'chmod +x gradlew'
            }
        }
        stage('Compile') {
            steps {
                sh './gradlew compileJava'
            }
        }
        stage('Unit Tests') {
            steps {
                sh './gradlew test'
            }
        }
    }
}
