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
        choice(name: 'ACTION', choices: ['frontend', 'backend'], description: 'Choose ansible Action')
    }

    stages {

        stage('ansible Action') {
            parallel {

                stage('frontend') {
                    steps {
                        git branch: 'main', url: 'https://github.com/vijayavanisabbiti/expense-ansible'
                        sh 'ansible-playbook -i ${component}.vijayavanimanju.online, expense.yml -e env=dev -e role_name=${component} -e ansible_user=centos -e ansible_password=DevOps321'

                    }
                }

                stage('backend') {
                    steps {
                        git branch: 'main', url: 'https://github.com/vijayavanisabbiti/expense-ansible'
                        sh 'ansible-playbook -i ${component}.vijayavanimanju.online, expense.yml -e env=dev -e role_name=${component} -e ansible_user=centos -e ansible_password=DevOps321'

                    }
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}