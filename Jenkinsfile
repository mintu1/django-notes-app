@Library("shared") _
pipeline{
    agent any
    
    stages{
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code"){
            steps{
                script{
                    clone("https://github.com/mintu1/django-notes-app.git, "main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    build("notes-app","latest")
                }
            }
        }
        stage("Push"){
            steps{
                script{
                    push("notes-app", "latest")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "this is for deploying the code"
                sh "docker compose down && docker compose up -d" 
            }
        }
    }
}
