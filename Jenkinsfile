stage('Run ansible script') {
   steps {
        ansiblePlaybook(
            playbook: "${env.PLAYBOOK_ROOT}/deploy_service.yaml",
            inventory: "${env.PLAYBOOK_ROOT}/${env.INVENTORY}",
          }
}
