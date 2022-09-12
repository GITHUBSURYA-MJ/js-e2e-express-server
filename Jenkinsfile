pipeline {
    agent { label 'tomcat' }
    stages {
        stage('SCM Checkout') {
            steps{
            git url: 'https://github.com/InnaPavan/js-e2e-express-server.git', branch: "main"
            }
        }
         
         stage('Build Image') {
             steps {
                 script {
                     dockerImage = docker.build("innapavan/nodeexpress:v1")
                    }
                 }
             }

         stage('Push Image') {
             steps {
                 script {
                     docker.withRegistery('', 'docke_id')
                       {
                     dockerImage.push()
                    }
                 }
             }
           }
         }
     }
