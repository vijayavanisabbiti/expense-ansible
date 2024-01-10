pipeline {
    agent {
        node {
            label "workstation"
        }
    }

    options {
        ansiColor('xterm')
    }

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['frontend', 'backend'], description: 'Choose ansible Action')
    }

    stages {

        stage('ansible Action') {
            steps {
                git branch: 'main', url: 'https://github.com/vijayavanisabbiti/expense-ansible'
                sh 'ansible-playbook -i http://internal-dev-backend-1744742493.us-east-1.elb.amazonaws.com/, expense.yml -e env=dev -e role_name=${ENVIRONMENT} -e ansible_user=centos -e ansible_password=DevOps321'

            }
        }

/*        stage('backend') {
            steps {
                git branch: 'main', url: 'https://github.com/vijayavanisabbiti/expense-ansible'
                sh 'ansible-playbook -i backend.vijayavanimanju.online, expense.yml -e env=dev -e role_name=backend -e ansible_user=centos -e ansible_password=DevOps321'

            }
        }*/
    }

    post {
        always {
            cleanWs()
        }
    }
}