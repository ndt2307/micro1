pipeline {
    agent any
    stages {
        stage('SSH to Remote Host') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'jenkins-ssh-key-for-abc',
                                                  keyFileVariable: 'SSH_KEY_FOR_ABC')]) {
                    sh '''
                    ssh -i $SSH_KEY_FOR_ABC -o StrictHostKeyChecking=no user@remote-server << EOF
                      echo "Hello from Jenkins!"
                      hostname
                      uptime
                    EOF
                    '''
                }
            }
        }
    }
}

