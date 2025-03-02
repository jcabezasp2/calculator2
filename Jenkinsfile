pipeline {
    agent {
        docker {
            image 'gradle:6.6.1-jre14-openj9'
            // We mount the Docker socket to allow DinD
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/jcabezasp2/calculator2.git'
            }
        }
        stage('Compile') {
            steps {
                sh 'gradle compileJava'
            }
        }
        stage('Unit Tests') {
            steps {
                sh 'gradle test'
            }
        }
    }
}