pipeline {
    agent any

    tools {
        maven 'Maven 3.9.11'
        git 'Git'
        git url: 'https://github.com/yamjalkiran/maven_sample_project.git',
         branch: 'main',
          credentialsId: 'yamjalkiran@gmail.com'
        
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/yamjalkiran/maven_sample_project.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Report') {
            steps {
                junit '**/target/surefire-reports/*.xml'
            }
        }
    }

    post {
        success {
            echo 'Build and tests succeeded!'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}



