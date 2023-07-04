pipeline{
    agent any
    environment{
        env_url = "practice.google.com"
        SSHCRED = credentials('SSH_CRED')
    }
    parameters{
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    //triggers{pollSCM('*/1 * * * *')}

    stages{
       stage('parallel stages'){
          parallel{
             stage('parallel 1'){
               steps{
                  echo "In parallel 1"
                  sleep 15
               }
             }
             stage('parallel 2'){
                steps{
                  echo "In parallel 2"
                  sleep 15
                }
             }
             stage('parallel 3'){
                steps{
                  echo "In parallel 3"
                  sleep 15
                }
             }
          }
        }
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
        // input {
        //       message "should we continue?"
        //       ok "Yes, we should"
        //       submitter "alice,bob"
        //       parameters{
        //         string(name: 'Person', defaultValue: 'Mr Jenkins', description: 'who should say hello to?')
        //       }
        //}
        steps{
            echo "This is stage 2"
            echo "Name of URL is ${env_url}"
         }
      }
      stage("Stage three"){
        when { 
            anyof {
             branch 'dev'
             changeset "**/*.js"
            }
        }
        steps{
            sh '''
            echo "This is stage 3"
            echo "Name of URL is ${env_url}"
            echo -e "\\e[32m Hi \\e[0m"

            '''
        }
      }
      stage("stage four"){
        steps{
            sh '''
            echo "this is stage 4"
            echo "Name of the url is ${env_url}"
            echo -e "\\e[32m Hello stage 4\\e[0m"

            '''
        }
      }
    }
}