pipeline {
    agent {
        label 'ansiblededicated'
    }
    stages {
        stage('Checkout') {
            steps {
                
                     checkout scmGit(branches: [[name: 'refs/heads/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Aishu937/ansible_nginx_jenkinx.git']])
                    //git branch: 'refs/heads/main', url: 'https://github.com/Aishu937/ansible_nginx_jenkinx.git'
            }
        }
        stage('Ansible Playbook Execution') {
            steps {
                sh 'ansible-playbook  $WORKSPACE/master.yml'
            }
        }
    }
    post {
        always {
            // Clean the workspace after the build
            cleanWs()
        }
    }
}
