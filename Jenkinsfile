pipeline {
    agent any

    tools {
        jdk 'JDK-17' // Make sure this name matches the JDK name in Jenkins (Manage Jenkins > Global Tool Configuration)
        maven 'Maven-3.8.8' // Same here for Maven
        git 'Defaultgit'
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/Karthyayeni/MyJavaProject.git'
            }
        }

        stage('Build & Test') {
            steps {
                sh 'mvn clean test'
            }
        }

        stage('Test Report') {
            steps {
                junit '**/target/surefire-reports/*.xml'
            }
        }
    }

    post {
        always {
            echo 'Build finished'
        }
    }
}