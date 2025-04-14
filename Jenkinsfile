pipeline {
    agent any

    tools {
        maven 'Maven_3.8.1'
        jdk 'JDK_11'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-username/my-maven-project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
    }
}