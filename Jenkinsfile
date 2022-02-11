node{
    stage('Clone') {
        checkout scm
    }
    
    stage('Init') {
        sh "apk add ansible sshpass"
        sh "rm -rf /root/.ssh"
        sh "echo '192.168.56.102 app-salaireee.imene.form' > /etc/hosts"
        sh "ssh-keygen -q -t rsa -N '' -f ~/.ssh/id_rsa"
        sh "sshpass -p 'Admin.' ssh-copy-id -o stricthostkeychecking=no root@app-salaireee.imene.form"
    }

    stage('Ansible') {
      ansiblePlaybook (
          colorized: true, 
          become: true,             
          playbook: 'playbook.yml',
          inventory: 'hosts.yml'
      )
    }
}
