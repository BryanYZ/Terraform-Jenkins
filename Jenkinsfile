pipeline {

    parameters {
        booleanParam(name: 'autoApprove', defaultValue: false, description: 'Automatically run apply after generating plan?')
    } 
    environment {
        AWS_ACCESS_KEY_ID     = credentials('AWS_ACCESS_KEY_ID')
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
    }

   agent  any
    stages {
        stage('checkout') {
            steps {
                 script{
                        dir("terraform")
                        {
                            git "https://github.com/BryanYZ/Terraform-Jenkins.git"
                        }
                    }
                }
            }
        stage('Install Terraform') {
            steps {
                script {
                    def terraformVersion = '1.7.4' ## you can define whatever req version you need
                    sh "wget https://releases.hashicorp.com/terraform/${terraformVersion}/terraform_${terraformVersion}_linux_amd64.zip"
                    sh "unzip -o terraform_${terraformVersion}_linux_amd64.zip"
                    sh 'chmod +x terraform'
                    sh 'mv terraform /usr/local/bin/terraform'
                    sh 'terraform version'
                }
            }
        }


    }

}
