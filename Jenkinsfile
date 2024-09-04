pipeline {
    agent any

    parameters {
        string(name: 'CONTAINER_NAME', defaultValue: 'nginx-container', description: 'Name of the Docker container')
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mohamed00mamdouh/container_made_by_terra.git'
            }
        }

        stage('Update tfvars') {
            steps {
                script {
                    writeFile file: 'terraform.tfvars', text: "container_name = '${CONTAINER_NAME}'\n"
                }
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply '
            }
        }
    }
}
