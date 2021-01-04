pipeline {
  agent any
  environment {
    PATH = "${PATH}:${getTerraformPath()}"
  }

stages {
  
  stage ('S3 - create bucket'){
    steps {
      sh "ansible-playbook s3-bucket.yml"
        }
     }

  stage ('Execute Ansible Playbook'){
    steps {
      sh "ansiblePlaybook credentialsId: 'private-key', disableHostKeyChecking: true, installation: 'ansible', inventory: 'dev.inv', playbook: 's3-bucket.yml'"
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
