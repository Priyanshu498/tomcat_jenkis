pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                // Checkout the code from your Git repository
                git branch: 'main', url: 'https://github.com/Priyanshu498/Final-tool-tomcat.git'
            }
        }

        stage('Dryrun Playbook') {
            steps {
                // Use SSH credentials to run the dry run of the Ansible playbook
                withCredentials([sshUserPrivateKey(credentialsId: 'ubuntu', keyFileVariable: 'SSH_PRIVATE_KEY')]) {
                    sh '''
                    ansible-playbook -i ./assignmet_0n_tool/tomcat/tests/inventory ./assignmet_0n_tool/tomcat/tests/test.yml --check
                    '''
                }
            }
        }

        stage('Execute Playbook') {
            input {
                message "Do you want to proceed with the actual run?"
                ok "Yes"
            }
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'ubuntu', keyFileVariable: 'SSH_PRIVATE_KEY')]) {
                    sh '''
                    ansible-playbook -i ./assignmet_0n_tool/tomcat/tests/inventory ./assignmet_0n_tool/tomcat/tests/test.yml
                    '''
                }
            }
        }
    }
}
