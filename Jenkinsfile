pipeline {
    agent any
    stages {
        stage('SSH to Remote Host') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'jenkins-ssh-key-for-abc',
                                                  keyFileVariable: 'SSH_KEY_FOR_ABC')]) {
                    sh '''#!/bin/bash
                        echo "hello world"
                        ls
                        echo $SSH_KEY_FOR_ABC
                        echo "hello world"
                        ssh -i $SSH_KEY_FOR_ABC -o StrictHostKeyChecking=no vagrant@192.168.56.101 << EOF
                      echo "Hello from Jenkins!"
                      hostname
                      uptime
                    EOF
                    '''
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

