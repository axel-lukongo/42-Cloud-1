pipeline {
    agent any
    triggers {
        pollSCM('* * * * *') // Scrute le référentiel toutes les minutes
    }
    stages {
        stage('clone') {
            steps {
                git 'https://github.com/axel-lukongo/42-Cloud-1.git'
            }
        }
        stage('deploye') {
            steps {
              script{
                  sh '/Users/axellukongo/test/42-Cloud-1/ansible-playbook -i inventories/host.yml playbook.yml'
              }
            }
        }
    }
}