pipeline {
    agent { any }
    stages {
        stage('run ansible playbook') {
            steps {
                sh 'ansible-playbook -i hosts tomcat-setup.yml --ask-become-pass'
            }
        }
    }
}
