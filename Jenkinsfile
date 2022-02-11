node{
    stage('Clone') {
        checkout scm
    }
    stage('Ansible') {
      ansiblePlaybook (
          colorized: true, 
          become: false,             
          playbook: 'playbook.yml',
          inventory: 'hosts.yml'
      )
    }
}
