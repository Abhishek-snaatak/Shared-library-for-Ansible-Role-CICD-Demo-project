@Library('ansible-role-ci-shared-lib') _

pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Abhishek-snaatak/Shared-library-for-Ansible-Role-CICD-Demo-project'
            }
        }

        stage('Ansible Role CI') {
            steps {
                // Call shared library directly
                ansibleRoleCI(
                    roleName: 'roles',
                    testPlaybook: 'tests/test.yml'
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
