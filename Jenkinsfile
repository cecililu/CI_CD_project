// pipeline {
//     agent any

//     stages {
//         stage('Test') {
//             steps {
//                 sh 'echo "Test skipped"'
//             }
//         }

//         stage('Build and Publish Docker Image') {
//             steps {
//                 echo "Building and Publishing Docker image using Docker Build and Publish plugin"
//                 script {
//                     def dockerImage = docker.build("your_docker_image_name:your_image_tag", "-f .")

//                     // Log in to Docker Hub with your credentials
//                     withCredentials([usernamePassword(credentialsId: 'doc-hub', usernameVariable: 'DOCKER_HUB_USERNAME', passwordVariable: 'DOCKER_HUB_PASSWORD')]) {
//                         dockerImage.push("${DOCKER_HUB_USERNAME}", "${DOCKER_HUB_PASSWORD}")
//                     }
//                 }
//             }
//         }
//     }

//     post {
//         success {
//             echo 'Success'
//         }
//         failure {
//             echo 'Failed'
//         }
//         unstable {
//             echo 'Unstable'
//         }
//         changed {
//             echo 'State changed'
//         }
//     }
// }
pipeline {
    agent any
         stages {
           
                stage('github checkout code'){
                    steps(){
                        checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'githubcecil', url: 'https://github.com/cecililu/CI_CD_project']])
                    }
                }
                stage("build docker image"){
                    steps{
                        script{
                             sh 'docker build -t docker-cicd:v1 .'
                             
                        }
                    }
                }
            
         }
    }