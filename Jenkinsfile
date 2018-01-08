pipeline {
    agent none
    stages {
        stage('Validate') {
            agent { docker 'hashicorp/packer:full' }
            steps {
                echo 'Validating Machine Image Definition'
                sh 'packer validate packer.json'
            }
        }
        stage('Build') {
            agent { docker 'hashicorp/packer:full' }
            environment {
                CI_AWS_KEYS = credentials('CI_AWS_KEYS')
                AWS_ACCESS_KEY_ID = "${CI_AWS_KEYS_USR}"
                AWS_SECRET_ACCESS_KEY = "${CI_AWS_KEYS_PSW}"
            }
            steps {
                echo 'Build Machine Image'
                sh 'packer build -color=false packer.json'
            }
        }
    }
}