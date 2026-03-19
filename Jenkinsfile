pipeline {
    agent any
    tools {
        maven 'Maven3'
    }
    environment {
        DOCKERHUB_PWD = credentials('CredentialID_DockerHubPWD')
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/FAVOUROSEJI/comp367-lab2-dummy.git'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('Docker build') {
            steps {
                script {
                    bat 'docker build -t oseji/maven-webapp:1.0 .'
                }
            }
        }
        stage('Docker login') {
            steps {
                script {
                    bat 'docker login -u oseji -p %DOCKERHUB_PWD%'
                }
            }
        }
        stage('Docker push') {
            steps {
                script {
                    bat 'docker push oseji/maven-webapp:1.0'
                }
            }
        }
    }
    post {
        success {
            echo 'Build Successful'
        }
        failure {
            echo 'Build Failed'
        }
    }
}