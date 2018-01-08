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
    }
}