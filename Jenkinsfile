@Library("Shared") _
pipeline {
    agent any
    stages {
        stage("Code") {
            steps {
                script {
                    clone("https://github.com/amitkumar0128/docker-deploy-threeways.git","main")
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
