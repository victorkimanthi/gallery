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
        stage('Deploy to Heroku') {
          steps {
            withCredentials([usernameColonPassword(credentialsId: 'heroku', variable: 'HEROKU_CREDENTIALS' )]){
              sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/apps/app-gallery/deploy/heroku-git master'
            }
          }
        }
  }
}
