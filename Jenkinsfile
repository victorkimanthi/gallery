pipeline { 
  agent any
  tools {
      nodejs "20.3.1"
    }
  stages { 
    stage('clone repository') {
      steps {
      withCredentials([gitUsernamePassword(credentialsId: 'pipeline-gallery-credentials', gitToolName: 'Default')]) {
          git 'https://github.com/victorkimanthi/gallery'
      }
     }
    }
     stage('install dependencies') {
          steps {
            sh 'npm install'
          }
        }
        stage('Deploy to Heroku') {
          steps {
            withCredentials([usernameColonPassword(credentialsId: 'heroku', variable: 'HEROKU_CREDENTIALS' )]){
              sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/app-gallery.git master'
            }
          }
        }
  }
}
