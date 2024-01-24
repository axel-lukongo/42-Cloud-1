pipeline {
    agent any
    triggers {
        pollSCM('* * * * *') // Scrute le référentiel toutes les minutes
    }
    stages {
        stage('clone') {
            script {
              sh 'git clone https://github.com/axel-lukongo/42-Cloud-1.git'
            }
        }
        stage('deploye') {
            steps {
              script{
                  sh 'pwd rererere >> ~/test/nono'
              }
            }
        }
    }
}