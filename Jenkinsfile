pipeline {
    agent any

    tools {
        maven 'Maven'      // Make sure Maven is configured in Jenkins
        jdk 'JDK'          // Make sure JDK is configured
    }

    stages {

        stage('Checkout SCM') {
            steps {
                git 'https://github.com/Tusha06/Jenkin.git'
            }
        }

        stage('Initialize') {
            steps {
                bat 'echo Initializing project...'
                bat 'java -version'
                bat 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
        }
        success {
            echo 'Build Successful ✅'
        }
        failure {
            echo 'Build Failed ❌'
        }
    }
}
