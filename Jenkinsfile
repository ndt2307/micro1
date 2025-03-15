pipeline {
    agent any
    stages {
        stage('SSH to Remote Host') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'jenkins-ssh-key-for-abc',
                                                  keyFileVariable: 'SSH_KEY_FOR_ABC')]) {
                    sh '''#!/bin/bash
                    echo "hello world" 
                    '''
                    sh '''
                    ssh -i ~/.ssh/jenkins_ssh_key jenkinsdemo@192.168.56.101 hostname
                    '''
                }
            }
        }
    }
}

