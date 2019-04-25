pipeline {
  agent any
  stages {
    stage('Stage1') {
      parallel {
        stage('Build') {
          steps {
            addBadge(icon: 'Test Icon', text: 'Test python version')
          }
          steps {
            sh 'python --version'
          }
        stage('controller upgrade') {
          steps {
            sh 'python  /home/ubuntu/python/upgrade.py 52.53.113.44 4.2'
          }
        }
      }
    }
  }
}