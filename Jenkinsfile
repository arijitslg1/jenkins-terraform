pipeline {
  agent any
  environment {
    PATH = "${PATH}:${getTerraformPath()}"
  }

stages {

  stage ('Execute Ansible Playbook'){
    steps {
      ansiblePlaybook become: true, credentialsId: 'private-key', disableHostKeyChecking: true, installation: 'ansible', inventory: 'dev.inv', playbook: 's3-bucket.yml'
       }
     }
   

  stage ('terraform init'){
    steps {
        sh "terraform init"
        }
     }
  
  }
}

def getTerraformPath(){
  def tfHome = tool name: 'TERRAFORM_HOME', type: 'org.jenkinsci.plugins.terraform.TerraformInstallation'
  return tfHome
}
