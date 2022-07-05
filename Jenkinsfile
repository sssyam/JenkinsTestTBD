pipeline{
    agent any
    stages{
        stage ("build"){
            steps{
                echo "Building the application"
                sh "docker compose build"
            }
        }

        stage ("deploy"){
            steps{
                echo "Deploy the application"
                sh "docker compose up -d"
            }
        }

        stage ("test"){
            steps{
                echo "Testing the application"
                sh '''
                    curl localhost
                    "x$?" -eq "x0" && echo "test worked" || echo "test failed"
                '''
            }
        }

        stage ("clean"){
            steps{
                echo "cleaning up"
                sh "docker compose down"
            }
        }
    }
}

node{
    // Groovy script
}