pipeline {
  agent any
  stages {
    stage ('terraform init'){
      steps {
        sh "terraform init"
        }
     }
  }
}
<<<<<<< HEAD
=======

def getTerraformPath(){
  def tfHome = tool name: 'TERRAFORM_HOME', type: 'org.jenkinsci.plugins.terraform.TerraformInstallation'
  return tfHome
}
>>>>>>> a1531f047f05058fe961e7007c0b4bc8b57e2ae9
