pipeline{
    agent any
    stages{
        stage ("build"){
            steps{
                echo "Building the application"
                sh "docker-compose build"
            }
        }

        stage ("deploy"){
            steps{
                echo "Deploy the application"
                sh "docker-compose up --build &"
            }
        }

        stage ("test"){
            steps{
                echo "Testing the application"
                sh """
                    curl localhost
                    $? -eq 0 && echo "test worked" || echo "test failed"
                """
            }
        }
    }
}

node{
    // Groovy script
}