pipeline{
    agent any
    environment{
        env_url = "practice.google.com"
        SSHCRED = credentials('SSH_CRED')
    }
    // 

    triggers{pollSCM('*/1 * * * *')}

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
        input {
              message "should we continue?"
              ok "Yes, we should"
              submitter "alice,bob"
              parameters{
                string(name: 'Person', defaultValue: 'Mr Jenkins', description: 'who should say hello to?')
              }
        }
        steps{
            echo "This is stage 2"
            echo "Name of URL is ${env_url}"
         }
      }
      stage("Stage three"){
        when {branch 'dev'}
        steps{
            sh '''
            echo "This is stage 3"
            echo "Name of URL is ${env_url}"
            echo -e "\\e[32m Hi \\e[0m"

            '''
        }
      }
      stage("stage four"){
        step{
            sh '''
            echo "this is stage 4"
            echo "Name of the url is ${env_url}
            echo -e "\\e[32m Hello stage 4\\e[0m"
            '''
        }
      }
    }
}