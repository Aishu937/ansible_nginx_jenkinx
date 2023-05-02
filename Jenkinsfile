pipeline {
    agent {
        label 'masternodes'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[url: 'https://github.com/Aishu937/ansiblerepo.git']]
                )
            }
        }
        stage('Ansible Playbook Execution') {
            steps {
                sh 'ansible-playbook  $WORKSPACE/install nginx and jenkins/nginx_install.yml'
            }
        }
    }
}
