@Library("shared_lib") _
pipeline {
    agent {label "master"}

    stages {
        stage('hello'){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('Code') {
            steps {
                script{
                     cloning("https://github.com/LikhithSM/node-todo-cicd.git","master")
                }
            }
        }
        stage('Build') {
            steps {
                script{
                    build("my-notes","latest","likhithsm")   
                }
            }
        }
        stage('Push to docker hub') {
            steps {
                script{
                    push('my-notes','latest')
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the code'
                //sh 'docker run -d -p 8000:8000 my-notes:latest'
                sh 'docker compose up -d'
            }
        }
    }
}
