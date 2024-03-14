pipeline {
    agent any
    triggers {
        cron('H/10 * * * 4')
    }
    tools {
        maven 'Maven 3.6.3'
        jdk 'OpenJDK 11'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh 'mvn clean package'
                }
            }
        }
        stage('Test with JaCoCo') {
            steps {
                script {
                    sh 'mvn test jacoco:report'
                }
            }
        }
    }
    post {
        always {
            jacoco(execPattern: '**/target/site/jacoco/jacoco.xml')
        }
    }
}
