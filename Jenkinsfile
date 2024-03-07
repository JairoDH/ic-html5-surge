pipeline {
    environment {
        TOKEN = credentials('SURGE_TOKEN')
    }
    agent {
        docker { 
            image 'josedom24/debian-npm'
            args '-u root:root'
        }
    }
    stages {
        stage('Clone') {
            steps {
                git branch: 'master', url: 'https://github.com/JairoDH/ic-html5-surge.git'
            }
        }
        stage('Install surge') {
            steps {
                sh 'npm install -g surge'
            }
        }
        stage('Deploy') {
            steps {
                sh "surge ./_build/ jairodh.surge.sh --token ${TOKEN}"
            }
        }
    }
}

