pipeline {
    agent any

    stages {
        stage('Docker Build') {
            steps {
                script {
                    sh """
                    cd $WORKSPACE/creative

                    sudo docker build -t test .
                    sudo docker images

                    docker build -t test .
                    docker images

                    """
                }
            }
        }

        stage('Docker Deploy') {
            steps {
                script {
                    sh """

                        sudo docker run -itd -p 80:80 test:latest
                        sudo docker ps 
                        sudo docker ps -
                        sudo docker run -itd -p 80:80 test:latest
                        sudo docker ps 
                        sudo docker ps -a

                    """
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}