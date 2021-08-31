pipeline {
    agent any
    environment{
        DATABASE_URI = credentials('DB-URI')
        SECRET_KEY = credentials('secretkey')
    }
    stages {
        stage('Build') {
            steps {
                sh ' docker build '
            }
        }
        stage('Test') {
            steps {
                //
            }
        }
        stage('Deploy') {
            steps {
             sh 'docker push IMAGE'
             SH 'docker run IMAGE'
            }
        }
    }
}
