// node {
//     def app
//     stage('Clone repository') {
//         checkout scm
//     }
//     stage('Build image') {
//        app = docker.build("kbogojoska/kiii-jenkins")
//     }
//     stage('Push image') {   
//         docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
//             app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
//             app.push("${env.BRANCH_NAME}-latest")
//             // signal the orchestrator that there is a new version
//         }
//     }
// }
pipeline {
    agent any
    
    stages {
        stage('Clone repository') {
            steps {
                checkout scm
            }
        }
        stage('Build image') {
            steps {
                script {
                    def app = docker.build("kbogojoska/kiii-jenkins")
                }
            }
        }
        stage('Push image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
                        app.push("${env.BRANCH_NAME}-latest")
                        // Signal the orchestrator that there is a new version
                    }
                }
            }
        }
    }
}
