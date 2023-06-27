pipeline{
    agent any
    environment{
        env_url = "practice.google.com"
        SSHCRED = credentails('SSH_CRED')
    }
    stages{
      stage('Stage one'){
         steps {
            sh '''
                echo AWS practice
                echo Devops pratice
                echo Name of URL is ${env_url}
                env
            '''
         }
      }
      stage('Stage two'){
        environment{
               env_url= "stage.google.com"
        }
        steps{
            echo "This is stage 2"
            echo "Name of URL is ${env_url}"
         }
      }
      stage("Stage three"){
        steps{
            echo "This is stage 3"
            echo "Name of URL is ${env_url}"
        }
      }
    }
}