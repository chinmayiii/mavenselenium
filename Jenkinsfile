pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/chinmayiii/mavenselenium.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Run Application') {
            steps {
                sh 'mvn exec:java'
            }
        }
    }

    post {
        success {
            script {
                currentBuild.description = """
                <a href="https://www.saucedemo.com" target="_blank">
                Open SauceDemo
                </a>
                """
            }
        }

        failure {
            echo "Build Failed"
        }
    }
}
