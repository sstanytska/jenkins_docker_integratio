pipeline {
    agent{
        docker{
            image "wordpress"
            label "docker1"
        }
    }
    parameters {
        string(defaultValue: "Testfile",  name: "What_File_To_Write",  description: "What file should I write? ")
        string(defaultValue: "Hello world",  name: "What_To_Write",  description: "What should I write? ")
    }
    triggers{
        pollSCM('* * * * * ')
    }
    stages{
        stage("Git Pull"){
            steps{
                git 'https://github.com/farrukh90/terraform.git'
            }
        }
        stage("Hello"){
           steps{
               ws("${workspace}/tmp"){
                   sh '''
                   set +xe
                   echo Hello
                   touch file
                   mkdir folder
                   cat /etc/passwd  > users
                   '''
               }
           }
        }
        stage("write to a file"){
            steps{
                writeFile file: 'testfile', text: 'This is test'
            }
        }
    }
}
