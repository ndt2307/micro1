pipeline {
    agent any
    stages {
        stage('SSH to Remote Host') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'jenkins-ssh-key-for-abc',
                                                  keyFileVariable: 'SSH_KEY_FOR_ABC')]) {
		    script {
                        echo "SSH Key Path: ${env.SSH_KEY_FOR_ABC}"
                    }
                    sh '''
	            echo $SSH_KEY_FOR_ABC
		    ping 192.168.56.101
                    ssh -vvv -i $SSH_KEY_FOR_ABC -o StrictHostKeyChecking=no -tt jenkinsdemo@192.168.56.101 << EOF
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

