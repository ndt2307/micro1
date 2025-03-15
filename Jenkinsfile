pipeline {
    agent any
    stages {
        stage('SSH to Remote Host') {
            steps {
                script {
                    withCredentials([sshUserPrivateKey(credentialsId: 'jenkins-ssh-key-for-abc',
                                                  keyFileVariable: 'SSH_KEY_FOR_ABC')]) {
                        sshCommand remote: [
                            credentialsId: 'jenkins-ssh-key-for-abc',
                            host: '192.168.56.101',
                            user: 'vagrant',
                            name: 'vagrant'
                        ], command: "hostname && uptime"
                    }
                }
            }
        }
    }
}

