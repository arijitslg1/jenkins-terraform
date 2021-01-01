pipeline {
  agent any
  environment {
    PATH = "${PATH}:${getTerraformPath()}"
  }

stages {
  stage ('S3 - create bucket'){
    steps {
      script {
        createS3Bucket('my-tf-test')
        }
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


def createS3Bucket(bucketName){
 sh returnStatus: true, script: "aws s3 mb ${bucketName} --region=us-east-1" 
}
