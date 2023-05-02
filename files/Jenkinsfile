pipeline {
    agent {
        label 'masternodes'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(
                    checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '2d99ebf5-3863-49ff-8454-278f4c185406', url: 'https://github.com/Aishu937/ansiblerepo.git']])
                )
            }
        }
        stage('Ansible Playbook Execution') {
            steps {
                sh 'ansible-playbook  $WORKSPACE/nginx_install.yml'
            }
        }
    }
}
