pipeline {
  agent any
  stages {
      stage('controller upgrade') {
          steps {
            sh 'python --version'
            addBadge(icon: 'Test Icon', text: 'Upgrade 4.3')
            sh 'python  /home/ubuntu/python/upgrade.py 52.53.113.44 4.3-patch'
            echo 'done upgrading the controller'
            // sh 'python3 /home/ubuntu/python/get_version_set_banner.py 52.52.113.44 "Reg43 Canada Transit Peering"'
          }
      }
      stage('Cluster0') {
          steps {
            addBadge(icon: 'Test Icon', text: 'Cluster0 Transit')
            build (job: 'tgw-peering-benchmark',
            parameters: [
            string(name: 'secret', value: '/home/ubuntu/52.53.113.44.secret.tfvars'),
            string(name: 'account', value: 'EdselAWS'),
            string(name: 'action', value: 'cluster0')
            ])
            addBadge(icon: 'Test Icon', text: 'Cluster0 Spoke')
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'action', value: 'cluster0_spoke')])
            addBadge(icon: 'Test Icon', text: 'Cluster0 TGW Spoke')
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'action', value: 'cluster0_tgw_spoke')])
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'action', value: 'cluster0_spoke_azure')])
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'action', value: 'cluster0_spoke_gcp')])
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'action', value: 'onprem')])
          }
      }
      stage('Cluster1') {
          steps {
            build job: 'tgw-peering-benchmark',
            parameters: [string(name: 'action', value: 'cluster1')]
          }
      }
      stage('Cluster2') {
          steps {
            build job: 'tgw-peering-benchmark',
            parameters: [string(name: 'action', value: 'cluster2')]
          }
      }
      stage('Cluster3') {
          steps {
            build job: 'tgw-peering-benchmark',
            parameters: [string(name: 'action', value: 'cluster3')]
          }
      }
      stage('Cluster4') {
          steps {
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'action', value: 'cluster4')])
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'action', value: 'cluster4_addTGW')])
          }
      }
      stage('Cluster5') {
          steps {
            addBadge(icon: 'Test Icon', text: 'Cluster5 Azure Transit')
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'action', value: 'cluster5')])
            addBadge(icon: 'Test Icon', text: 'Cluster5 Azure Spoke')
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'action', value: 'cluster5_spoke_azure')])
          }
      }
      stage('Cluster6') {
          steps {
            addBadge(icon: 'Test Icon', text: 'Cluster6 Insane Transit')
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'action', value: 'cluster6')])
            addBadge(icon: 'Test Icon', text: 'Cluster6 Insane Spoke')
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'action', value: 'cluster6_insanespoke')])
            addBadge(icon: 'Test Icon', text: 'Cluster6 NonInsane Spoke')
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'action', value: 'cluster6_noninsanespoke')])
          }
      }
      stage('Cluster7') {
          steps {
            addBadge(icon: 'Test Icon', text: 'Cluster Insane Transit2')
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'action', value: 'cluster7')])
          }
      }
      stage('Transit Peering') {
          steps {
            addBadge(icon: 'Test Icon', text: 'transit peering')
            build (job: 'tgw-peering-benchmark', parameters: [string(name: 'peering', value: 'transitX-6mesh')])
          }
      }
      /*
      stage('Datacheck') {
          steps {
            addBadge(icon: 'Test Icon', text: 'datacheck')
            build (job: 'tgw-peering-benchmark', parameters: [booleanParam(name: 'datacheck', value: true)])
          }
      }
      */
  }
}