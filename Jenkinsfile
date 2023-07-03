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
    triggers{pollSCM('H/1 * * * *')}
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
            sh '''
            echo "This is stage 3"
            echo "Name of URL is ${env_url}"
            echo -e "\\e[32m Hi \\e[0m"

            '''
        }
      }
    }
}