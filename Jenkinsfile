@Library("shared") _
pipeline{
    agent {label "agent-jenkins"}
    
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
                    clone('https://github.com/mimqupspy/django-notes-app.git','main')
                    echo "Clone Sucessfully"
                }
            }
        }
        stage("Build"){
            steps{
               script{
                   docker_build("noteapp","latest","internaldev")
               }
            }
        }
        
        stage("Test"){
            steps{
                echo "This is test the code"
            }
        }
        stage("Push to Docker Hub"){
            steps{
             script{
                 docker_push("noteapp","latest","internaldev")
             }
            }
        }
        stage("Deploy"){
            steps{
                echo "this is deploy the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
