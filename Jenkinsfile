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
                def workspace = "/Users/axellukongo/.jenkins/workspace/p1"
                sh 'ansible-playbook -i inventories/host.yml $workspace/playbook.yml'
              }
            }
        }
    }
}