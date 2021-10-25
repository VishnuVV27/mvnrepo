pipeline {
    agent any
    tools {maven 'mvn'}
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                bat './jenkins/scripts/deliver.bat'
            }
        }
         stage('output') {
            steps {
                bat './jenkins/scripts/java.bat'
            }
        }
    }
}
