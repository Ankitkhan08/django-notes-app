@Library("Shared") _
pipeline {
    agent {label "vinod"}
    
    stages {
        stage('hello')
        {
            steps
            {
                script
                {
                    hello()
                }
            }
        }
        stage('Code') {
            steps 
            {
               script
               {
                   clone("https://github.com/Ankitkhan08/django-notes-app.git","main")
               }
            }
        }
        stage('Build') {
            steps 
            {
                script
                {
                    docker_build('notes-app','latest','ankitkhan')
                }
            }
        }
        stage('Push to DockerHub') {
            steps 
            {
                script
                {
                    docker_push('notes-app','latest','ankitkhan')
                }
            }
        }
        stage('Deploy') {
            steps 
            {
                echo "this is deploying the code" 
                sh "docker compose up -d"
            }
        }
    }
}
