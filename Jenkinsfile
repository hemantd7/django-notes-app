@Library("shared") _
pipeline {

    agent { label "zorro" }

    stages {
        
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code") {
            steps {
                script{
                    clone("https://github.com/hemantd7/django-notes-app.git","main")
                }
            }
        }

        stage("Build") {
            steps {
                script{
                docker_build("hemantdockerhub7", "notes-app","latest")
                }
            }
        }

        stage("Push to DockerHub") {
            steps{
                script{
                    docker_push("notes-app", "latest", "hemantdockerhub7")
                }
            }
        }

        stage("Deploy") {
            steps {
                echo "this is deploying the code"

                sh "docker compose up -d"
            }
        }
    }
}
