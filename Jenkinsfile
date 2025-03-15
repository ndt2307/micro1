pipeline {
    agent any
    stages {
        stage('SSH to Remote Host') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'jenkins-ssh-key-for-abc',
                                                  keyFileVariable: 'SSH_KEY_FOR_ABC')]) {
                    sh '''
                    ssh -i $SSH_KEY_FOR_ABC vagrant@192.168.56.101 hostname
                    '''
                }
            }
        }
    }
}

