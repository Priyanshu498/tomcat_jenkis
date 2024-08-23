pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Git repository se code checkout karna
                git 'https://github.com/Priyanshu498/tomcat_jenkis.git'
            }
        }
        stage('Install Tomcat') {
            steps {
                // Tomcat install script ko run karna
                sh 'bash path/to/your/tomcat-install-script.sh'
            }
        }
        stage('Verify Installation') {
            steps {
                // Verify Tomcat installation (example check)
                sh 'curl http://localhost:8080'
            }
        }
    }

    post {
        success {
            echo 'Tomcat installation was successful!'
        }
        failure {
            echo 'Tomcat installation failed.'
        }
    }
}
