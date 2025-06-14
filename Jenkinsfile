@Library("shared") _
pipeline{
    agent any

    tools {
        jdk 'jdk8'
        maven 'maven3'
    }
    environment {
        SCANNER_HOME = tool 'Sonar'
    }
    
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
                    clone("https://github.com/mintu1/django-notes-app.git", "main")
                }
            }
        }

        stage("Trivy"){
            steps{
                sh "trivy fs ."
            }
        }
        stage('File System Scan') {
            steps {
                sh "trivy fs --format table -o trivy-fs-report.html ."
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
            }
        }
    }
}
