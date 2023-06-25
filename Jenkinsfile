pipeline { 
  agent any
  stages { 
    stage('clone repository') {
      steps { 
        git 'https://github.com/victorkimanthi/gallery'
      }
    }
     stage('Build the project') {
          steps {
            sh 'npm install'
          }
        }
  }
}
