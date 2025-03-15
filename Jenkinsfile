pipeline {
    agent any
    stages {
        stage('SSH to Remote Host') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'jenkins-ssh-key-for-abc',
                                                  keyFileVariable: 'SSH_KEY_FOR_ABC')]) {
                    remote.identityFile = SSH_KEY_FOR_ABC
                    stage("SSH Steps Rocks!") {
                        writeFile file: 'abc.sh', text: 'ls'
                        sshCommand remote: remote, command: 'for i in {1..5}; do echo -n \"Loop \$i \"; date ; sleep 1; done'
                        sshPut remote: remote, from: 'abc.sh', into: '.'
                        sshGet remote: remote, from: 'abc.sh', into: 'bac.sh', override: true
                        sshScript remote: remote, script: 'abc.sh'
                        sshRemove remote: remote, path: 'abc.sh'
                    }
                }
            }
        }
    }
}

