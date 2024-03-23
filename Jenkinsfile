pipeline {
    agent any
    
    stages {
        stage ("checkout from GIT") {
            steps {
              
              git branch: 'main', credentialsId: 'PUT YOUR CREDENTIALID', url: 'Your Github Repo' 
            } 
        }
        stage('Install Terraform') {
            steps {
                script {
                    def terraformVersion = '1.3.1' ## you can define whatever req version you need
                    sh "wget https://releases.hashicorp.com/terraform/${terraformVersion}/terraform_${terraformVersion}_linux_amd64.zip"
                    sh "unzip -o terraform_${terraformVersion}_linux_amd64.zip"
                    sh 'chmod +x terraform'
                    sh 'mv terraform /usr/local/bin/terraform'
                    sh 'terraform version'
                }
            }
        }
        
        ## now you can use terraform init
        stage ("terraform init") {
            steps {
                sh 'terraform init'
            }
        }
    }
}

