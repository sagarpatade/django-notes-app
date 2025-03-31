@Library("shared") _
pipeline {
    agent { label 'sagar' }
    
  
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
                    clone("https://github.com/sagarpatade/django-notes-app.git","main")
                    
                
                }
                
                
            }
        }
        
        stage('Build') {
            steps {
                script{
                    docker_build("notes-app","latest", "sagarpatade1900")
                }
            
            }
        }
        
        stage('Push to DockerHub') {
           steps {
               
               script{
                   docker_push("notes-app", "latest", "sagarpatade1900")
               }
                
                
            }
        }
        
        stage('Deploy') {
            steps {
                echo "Deploying the application using Docker Compose"
                sh "docker compose down && docker-compose up -d"
                
            }
        }
    }
}
