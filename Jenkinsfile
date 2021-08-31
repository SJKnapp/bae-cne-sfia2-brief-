pipeline {
    agent any
    environment{
        DATABASE_URI = credentials('DB-URI')
        SECRET_KEY = credentials('secretkey')
    }
    stages {
        stage('Build') {
            steps {
                sh ' docker-compose build'
            }
        }
        stage('Test') {
            steps {
                //
            }
        }
        stage('Deploy') {
            steps {
             sh 'docker-compose up'
             
            }
        }
    }
}
