pipeline {
    agent any
    stages {
        stage('SSH to Remote Host') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'jenkins-ssh-key-for-abc',
                                                  keyFileVariable: 'SSH_KEY_FOR_ABC')]) {
                    def remote = [:]
                    remote.name = "vagrant"
                    remote.host = "192.168.56.101s"
                    remote.allowAnyHosts = true
                    remote.identityFile = SSH_KEY_FOR_ABC
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

