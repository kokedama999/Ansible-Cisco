pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                // Jenkins automatically pulls your code from GitHub here
                checkout scm
            }
        }

        stage('Syntax Check') {
            steps {
                sh 'ansible-playbook -i inventory/hosts.yml playbooks/config.yml --syntax-check'
            }
        }

        stage('Deploy Configuration') {
            steps {
                echo 'Deploying to Cisco Routers...'
                // Run the playbook
                sh 'ansible-playbook -i inventory/hosts.yml playbooks/config.yml'
            }
        }
    }
}
