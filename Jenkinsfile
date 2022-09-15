pipeline {
    agent { label 'tomcat' }
    environment {
		DOCKERHUB_CREDENTIALS=credentials('docke_id')
	}
    stages {
        stage('SCM Checkout') {
            steps{
            git url: 'https://github.com/InnaPavan/js-e2e-express-server.git', branch: "main"
            }
                 }
    	stage('Build') {
	    steps {
	     sh 'docker build -t innapavan/nodeapp:latest .'
			}
		}
     	stage('Login') {
        	steps {
	     sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
       	stage('Push') {
		steps {
		sh 'docker push innapavan/nodeapp:latest'
			}
		}

             }
     }

