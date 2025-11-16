pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    options {
        // Timeout counter starts after agent is allocated
        timeout(time: 10, unit: 'MINUTES') // au lieu de 1 seconde
    }
    environment {
        APP_ENV = "DEV"
    }
    stages {
        stage('Code Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/feryel2/jenkins-demo.git',
                    credentialsId: 'github-pat'
            }
        }
        stage('Code Build') {
            steps {
                bat 'mvn install -Dmaven.test.skip=true'
            }
        }
    }
    post {
        always {
            echo "======always======"
        }
        success {
            echo "=====pipeline executed successfully ====="
        }
        failure {
            echo "======pipeline execution failed======"
        }
    }
}
