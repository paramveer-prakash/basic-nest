pipeline {
    agent none
    environment {
        npm_config_cache = 'npm-cache'
        registry = 'paramveerprakash/docnest'
        creds = 'dockercreds'
        dockerImage = ''
    }
    stages {
        stage('Clone') {
            steps {
                checkout scm   
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        stage('Containerize') {
            steps {
                sh 'docker build -t paramveerprakash/docknest:latest'
            }
        }
    }
}
