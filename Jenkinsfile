pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/FAVOUROSEJI/comp367-lab2-dummy.git'
            }
        }
        stage('Build') {
            steps {
                echo "Building dummy project for COMP367"
            }
        }
        stage('Greeting') {
            steps {
                script {
                    def hour = new Date().format('HH', TimeZone.getTimeZone('UTC')).toInteger()
                    def greeting = hour < 12 ? "Good morning" : "Good afternoon"
                    echo "${greeting}, Favour! Welcome to COMP367"
                }
            }
        }
    }
}