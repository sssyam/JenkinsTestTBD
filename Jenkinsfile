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
                    if [ "x$?" == "x0" ]
                    then 
                        echo "test worked" 
                    else
                        echo "test failed"
                    fi
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