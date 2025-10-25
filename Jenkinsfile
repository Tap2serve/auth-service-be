// @Library("Shared") _
// pipeline {
//     agent any
//     stages {
//         stage("Hello") {
//             steps{
//                 script{
//                     script{
//                         hello()
//                     }
//                 }
//             }
//         }
//         stage("Code"){
//             steps{
//                 script{
//                     clone("https://github.com/Tap2serve/auth-service-be.git", "main")
//                 }
//                 //git url:"https://github.com/Tap2serve/auth-service-be.git", branch:"main"
//             }
//         }
//         stage("Debug Workspace") {
//             steps {
//                 sh "pwd"
//                 sh "ls -la"
//             }
//         }
//         stage("Build") {
//             steps {
//                 echo "This is Build Step"
//                 sh "whoami"
//                 sh "docker build -t auth-service:latest ."
//             }
//         }
//         stage("Push to DockerHub"){
//             steps {
//                 echo "This is pushing the image to docker hub"
//                 withCredentials([usernamePassword(
//                     'credentialsId':"DockerHubCred",
//                     passwordVariable: "dockerHubPass",
//                     usernameVariable: "dockerHubUser")]){
//                 sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass} "
//                 sh "docker image tag auth-service:latest ${env.dockerHubUser}/auth-service:latest"
//                 sh "docker push ${env.dockerHubUser}/auth-service:latest"
//                 }  
//             }
//         }
//         stage("Deploy"){
//             steps {
//                 echo "This is deploying the code"
//                 sh "docker compose up -d"
//                 // sh "docker run -d -p 8001:8001 auth-service:latest"
//             }
//         }
//     }
// }

@Library("Shared") _
pipeline {
    agent any
    stages {
        stage("Checkout"){
            steps {
                code_checkout("https://github.com/Tap2serve/auth-service-be.git", "main")
            }
        }
        stage("Docker Build"){
            steps {
                script {
                    docker_build("auth-service","latest", "aniketsinare")
                }
            }
        }
        stage("Docker Push"){
            steps {
                script {
                    docker_push("auth-service","latest", "aniketsinare")
                }
            }
        }
    }
}
