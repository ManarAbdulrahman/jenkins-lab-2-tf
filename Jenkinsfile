pipeline {
    agent {
        docker {
          image "bryandollery/terraform-packer-aws-alpine"
          args "-u root --entrypoint = '' "
        }
    }
    environment {
           CREDS = credentials('6c22797b-6e23-4779-984c-c18d46aade6b')
           WONER = "MANAR"
           AWS_ACCESS_KEY_ID= "${CREDS_USR}"
           AWS_SECRET_ACCESS_KEY= "${CREDS_PSW}"
           TF_NAMESPACE = "where-is-manar"
           AWS_PROFILE="kh-labs"
        }
    stages {
        stage ('build') {
            steps {
                sh "make init"
                
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
