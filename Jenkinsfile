pipeline {
    agent any

    tools {
        maven "Maven"
        jdk "JDK21"
    }

    stages {

        stage('Initialize') {
            steps {
                sh 'echo "JAVA_HOME = $JAVA_HOME"'
                sh 'echo "M2_HOME = $M2_HOME"'
                sh 'echo "PATH = $PATH"'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn -B clean package'
            }
        }
    }

    post {
        always {
            junit allowEmptyResults: true,
                  testResults: '**/surefire-reports/*.xml'
        }
    }
}
