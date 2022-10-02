pipeline {
    agent any
    environment {
                VERSION = "${env.BUILD_ID}"
		DOCKERHUB_CREDENTIALS=credentials('DockerHub_paws')
	}
    stages {
        stage('SCM Checkout') {
            steps{
            git url: 'https://github.com/GITHUBSURYA-MJ/js-e2e-express-server.git', branch: "main"
            }
                 }
    	stage('Build') {
	    steps {
	     sh 'docker build -t surya47/nodeapp:${VERSION} .'
			}
		}
     	stage('Login') {
        	steps {
	                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
       	stage('Push') {
		steps {
		sh 'docker push surya47/nodeapp:${VERSION}'
			}
		}

             }
     }


