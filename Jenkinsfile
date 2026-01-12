@Library('ansible-role-ci-shared-lib') _

pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Abhishek-snaatak/Shared-library-for-Ansible-Playbook-CI-Demo-project'
            }
        }

        stage('Ansible Playbook CI') {
            steps {
                ansibleRoleCI(
                    roleName: 'common',
                    playbook: 'playbooks/site.yml',
                    inventory: 'inventory/dev.ini',
                    rolesPath: 'playbooks/roles'
                )
            }
        }
    }

    post {
        success {
            echo 'Playbook CI Passed ✅'
        }
        failure {
            echo 'Playbook CI Failed ❌'
        }
    }
}
