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
	                //sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			sh "docker login -u surya47 -p ${DOCKERHUB_CREDENTIALS}"
			}
		}
       	stage('Push') {
		steps {
		sh 'docker push surya47/nodeapp:${VERSION}'
			}
		}
	 stage('deploy_Appliction as Docker Continer into dckr server'){
		 steps{
			 
                  sshagent(['Dockr_pem_key']) {
                  sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.9.58 docker rm -f nodeapp || true"
            
                  sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.9.58 docker run -d -p 3000:3000 --name nodeapp surya47/nodeapp:${VERSION}"
        
                  }
       
		 }
       
        
    }   

             }
     }


