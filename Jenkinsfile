pipeline {
agent any   // Run this pipeline on ANY available Jenkins agent/node

```
stages {

    stage('Checkout SCM') {
        steps {
            // Pulls code from the repository configured in Jenkins job
            // (SCM = Source Code Management, usually GitHub)
            // This ensures Jenkins has the latest playbooks + inventory
            checkout scm
        }
    }

    stage('Syntax Check') {
        steps {
            // Runs Ansible syntax validation ONLY (no changes applied)
            // This catches YAML errors, indentation issues, bad modules, etc.
            // Think of this as a "fail fast" safety step
            sh 'ansible-playbook -i inventory/hosts.yml playbook/config.yml --syntax-check'
        }
    }

    stage('Deploy Configuration') {
        steps {
            // Just a log message so you can see progress in Jenkins UI
            echo 'Deploying to Cisco Routers...'

            // Executes the actual Ansible playbook
            // This is where REAL changes happen on devices
            // Uses:
            // - inventory/hosts.yml → defines routers
            // - playbook/config.yml → defines what config to push
            sh 'ansible-playbook -i inventory/hosts.yml playbook/config.yml'
        }
    }
}
```

}
