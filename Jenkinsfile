@Library('ansible-role-ci-shared-lib') _

pipeline {
    agent any

    environment {
        ROLE_NAME = 'common'
        TEST_PLAYBOOK = 'tests/test.yml'
    }

    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/your-org/demo-role-repo.git'
            }
        }

        stage('Ansible Role CI') {
            steps {
                // Call shared library
                ansibleRoleCI(roleName: env.ROLE_NAME, testPlaybook: env.TEST_PLAYBOOK)
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
