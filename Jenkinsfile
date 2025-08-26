@Library("Shared") _
pipeline {
    agent any
    stages {
        stage("Code") {
            steps {
                script {
                    clone("https://github.com/amitkumar0128/terra-ansible-jenkins-docker.git","main")
                }
            }
        }
        stage("Deploy") {
            steps {
                script {
                    docker_deploy()
                }
            }
        }
    }
}