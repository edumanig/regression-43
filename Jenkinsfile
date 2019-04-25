pipeline {
  agent any
  stages {
    stage('Build') {
        steps {
            addBadge(icon: 'Test Icon', text: 'Test python version')
            sh 'python --version'
        }
    }
    stage('controller upgrade') {
        steps {
            sh 'python  /home/ubuntu/python/upgrade.py 52.53.113.44 4.2'
            echo 'hello'
            echo 'hello2'

        }
    }
  }
}