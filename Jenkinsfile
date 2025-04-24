pipeline {
    agent any

    options{
        githubPush()
    }
    tools {
        maven 'Maven-3.8.8' // Make sure this matches your installed Maven version in Jenkins
        jdk 'JDK-17' // Or 'JDK 17' depending on your setup
    }

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-token', url: 'https://github.com/Karthyayeni/JavaProject.git', branch: 'main'
            }
        }

        stage('Build & Test') {
            steps {
                echo 'Running Maven build and tests...'
                sh 'mvn clean install'
            }
        }

        stage('Test Report') {
            steps {
                echo 'Publishing JUnit test reports...'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
    }

    post {
        success {
            echo 'Build and Tests were successful'
        }
        failure {
            echo 'Something went wrong with the build or tests'
        }
    }
}
