pipeline {

    agent {
        docker {
            image "bryandollery/terraform-packer-aws-alpine"
            args "-u root --entrypoint = "" "
        }
    }
    environment {
                CREDS = credentials('8136ddf7-0291-4f78-99b3-15a5cf3d9288')
                WONER = "MANAR"
                
                TF_NAMESPACE = "where-is-manar"
                AWS_PROFILE="kh-labs"
            }
    stages {
 
        stage ('build') {
         
            steps {
                sh "make init"
                sh "make start"
                sh "make plan"
            }
        }
       
        stage ('release') {
            steps {
                sh "make apply"
                
              
            }
        }
    }
} 
