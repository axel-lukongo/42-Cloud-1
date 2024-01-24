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
        // stage('Install Ansible') {
        //     steps {
        //         // Installer Ansible (assurez-vous qu'Ansible est installé sur votre agent Jenkins)
        //         script {
        //             sh 'apt-get update -y && apt-get install ansible -y'  // Remplacez ceci par la commande appropriée selon votre distribution
        //         }
        //     }
        // }
        stage('deploye') {
            steps {
              script{
                  ansiblePlaybook(
                  inventory: '/Users/axellukongo/test/42-Cloud-1/inventories',  // Remplacez ceci par le chemin de votre inventaire Ansible
                  playbook: '/Users/axellukongo/test/42-Cloud-1/playbook.yml'  // Remplacez ceci par le chemin de votre playbook Ansible
                )
              }
            }
        }
    }
}