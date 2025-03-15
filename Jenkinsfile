pipeline {
    agent any
    stages {
        stage('SSH to Remote Host') {
            steps {
                script {
                    sshCommand remote: [
                        credentialsId: 'jenkins-ssh-key-for-abc',
                        host: '192.168.56.101',
                        allowAnyHosts: false,
                        user: 'vagrant',
                        name: 'vagrant'
                    ], command: 'hostname && uptime'
                }
            }
        }
    }
}

