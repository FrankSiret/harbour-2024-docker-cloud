pipeline {
    agent any

    tools {
        go 'go-1.22'
    }

    stages {
        stage('Build') {
            steps {
                sh 'go build main.go'
                sh 'ls -la'
                sh 'echo "Build done!!!"'
            }
        }

        stage('Deploy github-action') {
            environment {
                ANSIBLE_HOST_KEY_CHECKING = 'false'
            }
            steps {
                sh 'echo "Deploying github-action"'

                ansiblePlaybook credentialsId: 'tkey',
                                inventory: 'inventory.ini',
                                playbook: 'playbook.yml'

            }
        }

    }
}