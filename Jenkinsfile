pipeline {
    agent any
    triggers {
        cron('H/10 * * * 4') // This will trigger the build every 10 minutes on Thursdays
    }
    tools {
        // Just make sure these tool names are configured in your Jenkins global tools
        maven 'MAVEN3'
        jdk 'OracleJDK8'
    }
    stages {
        stage('Build') {
            steps {
                // Using bat for Windows-based systems, sh for Unix-based systems
                bat 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                // Assuming the 'test' phase is bound to JaCoCo in your Maven pom.xml
                bat 'mvn test'
            }
        }
    }
    post {
        always {
            // Assuming you have the JaCoCo plugin installed
            jacoco()
        }
    }
}
