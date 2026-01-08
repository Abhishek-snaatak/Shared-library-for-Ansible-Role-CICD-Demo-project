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

        stage('Ansible Role CI') {
            steps {
                ansibleRoleCI(
                    roleName: 'roles',
                    testPlaybook: 'playbooks/site.yml'
                )
            }
        }
    }

    post {
        success {
            echo 'Role CI Passed ✅'
        }
        failure {
            echo 'Role CI Failed ❌'
        }
    }
}
