pipeline {
    agent any
    triggers {
        cron('H/10 * * * 4')
    }
    tools {
        maven 'MAVEN3'
        jdk 'OracleJDK8'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    bat 'mvn clean package'
                }
            }
        }
        stage('Test with JaCoCo') {
            steps {
                script {
                    bat 'mvn test jacoco:report'
                }
            }
        }
    }
    post {
        always {
            // Insert appropriate command or script to publish the Jacoco report on Windows
        }
    }
}
