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
            steps {
                echo 'Build Machine Image'
                sh 'packer build packer.json'
            }
        }
    }
}