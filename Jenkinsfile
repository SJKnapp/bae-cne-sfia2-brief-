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
	      dir("frontend"){
	      	sh 'pip3 install -r requirements.txt'
	      	sh 'python3 -m pytest --cov application --cov-report html'
	      }
	      dir("backend"){
	      	sh 'pip3 install -r requirements.txt'
              	sh 'python3 -m pytest --cov application --cov-report html'
	      }
	   }
	}
	stage('Artifacts'){
	    steps {
		sh 'docker push sjknapp/project-backend-image:latest'
		sh 'docker push sjknapp/project-frontend-image:latest'
	    }	
    }  
        stage('Deploy') {
            steps {
             sh 'docker-compose up -d'
            }
        }
    }
}
