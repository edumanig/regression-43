pipeline {
  agent any
  stages {
  //  stage('Build') {
  //      steps {
  //          addBadge(icon: 'Test Icon', text: 'Test python version')
  //          sh 'python --version'
  //      }
  //  }
  //  stage('controller upgrade') {
  //      steps {
  //          sh 'python  /home/ubuntu/python/upgrade.py 52.53.113.44 4.2'
  //          echo 'done upgrading the controller'
  //      }
  //  }
    stage('Cluster0') {
          steps {
            build job: 'tgw-peering-benchmark',
            parameters: [
            string(name: 'secret', value: '/home/ubuntu/52.53.113.44.secret.tfvars'),
            string(name: 'account', value: 'EdselAWS'),
            string(name: 'action', value: 'cluster3')
            ]
          }
    }
  }
}