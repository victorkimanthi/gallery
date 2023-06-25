pipeline { 
  agent any
  tools {
      nodejs "20.3.1"
    }
  stages { 
    stage('clone repository') {
      steps { 
        git 'https://github.com/victorkimanthi/gallery'
      }
    }
     stage('install dependencies') {
          steps {
            sh 'npm install'
          }
        }
  }
}
