pipeline {
    agent any
    stages {
        stage('SSH to Remote Host') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'jenkins-ssh-key-for-abc',
                                                  keyFileVariable: 'SSH_KEY_FOR_ABC')]) {
                    sh '''
                    ssh -i var/jenkins_home/.ssh/jenkins_ssh_key vagrant@192.168.56.101 << EOF
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

