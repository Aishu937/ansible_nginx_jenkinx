pipeline {
    agent {
        label 'ansiblededicated'
    }
    stages {
        stage('Checkout') {
            steps {
                
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Aishu937/ansible_nginx_jenkinx.git']])
            
            }
        }
        stage('Ansible Playbook Execution') {
            steps {
                sh 'ansible-playbook  $WORKSPACE/master.yml'
            }
        }
    }
}
