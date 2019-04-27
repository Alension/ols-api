pipeline {
    agent any
    stages {
        stage('Run Unit Tests') {
            agent { docker 'openjdk:11-jdk' }
            steps {
                sh './auto/run-unit-tests'
            }
        }
        stage('Deploy to Test') {
        agent { docker 'aaronyunan/jdk11-awscli' }
            steps {
                sh './auto/deploy'
            }
        }
        stage('Deploy to QA') {
        agent { docker 'aaronyunan/jdk11-awscli' }
            steps {
                sh './auto/deploy'
            }
        }
        stage('Deploy to Production') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
            }
            steps {
                echo 'Done!'
            }
        }
    }
}
