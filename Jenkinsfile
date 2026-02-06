@Library("Shared") _
pipeline{
    agent{label "john"}
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/LondheShubham153/django-notes-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","aroob5166")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","aroob5166")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
            
        }
    }
}
