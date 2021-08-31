pipeline {
    agent any
    environment{
        DATABASE_URI = credentials('DB-URI')
        SECRET_KEY = credentials('secretkey')
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker-compose build'
            }
        }
	stage('Test'){
	    steps {
	      sh 'pip3 install -r requirements.txt'
	      sh 'python3 -m pytest'
	      sh 'python3 -m pytest --cov application --cov-report html'
	    }
	}  
        stage('Deploy') {
            steps {
             sh 'docker-compose -d up'
            }
        }
    }
}
