pipeline {
  agent { label "NODE1"}

    
  stages {
        
    stage('Git') {
      steps {
        git branch: 'main', url: 'https://github.com/InnaPavan/js-e2e-express-server.git'
      }
    }
     
    stage('Build') {
      steps {
        sh 'npm install'
        
      }
    }  
            
  }
}