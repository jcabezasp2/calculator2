pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'gradle:6.6.1-jre14-openj9'
                    args '-v $HOME/.gradle:/home/gradle/.gradle'
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
    }
}