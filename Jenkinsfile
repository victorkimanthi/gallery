pipeline {

environment {
   siteLink = 'https://app-gallery-b1af698fffe2.herokuapp.com/'
}
  agent any
  triggers {
  pollSCM('0 */4 * * 1-5')
  }
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
              sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/app-gallery.git master'
            }
          }
        }
  }
  post {
      success {
          slackSend channel: '#victork_ip1',
                    color: 'good',
                    message: "The pipeline ${currentBuild.fullDisplayName} build ${env.BUILD_NUMBER} completed successfully.The site link is ${siteLink}"
      }
  }
}
