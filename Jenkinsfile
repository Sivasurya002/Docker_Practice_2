pipeline
{
    agent any
    stages
    {
        stage( "clean" )
        {
            steps
            {
                script
                {
                    sh ' rm -rf /var/lib/jenkins/workspace/Docker_practice_2/* '
                }

                // Clean containers
                script {
                    // Check if any container is running
                    def containerExists = sh(script: 'docker ps -q', returnStatus: true) == 0

                    // If containers exist, stop and remove them
                    if (containerExists) {
                        sh 'docker stop $(docker ps -a -q)'
                        sh 'docker rm $(docker ps -a -q)'
                        echo 'Containers removed successfully.'
                    } else {
                        echo 'No containers to remove.'
                    }
                }
                
                // Clean images
                script {
                    // Check if any images are present
                    def imageExists = sh(script: 'docker images -q', returnStatus: true) == 0

                    // If images exist, remove them
                    if (imageExists) {
                        sh 'docker rmi $(docker images -q)'
                        echo 'Images removed successfully.'
                    } else {
                        echo 'No images to remove.'
                    }
                }
            }
        }
        stage( "Clone" )
        {
            steps
            {
                sh ' git clone https://github.com/Sivasurya002/Docker_Practice_2.git '
                
                // sh ' docker stop $(docker ps -a -q) '
                // sh ' docker rm $(docker ps -a -q) '
                // sh ' docker rmi $(docker images -q) '
                // withCredentials([string(credentialsId: 'f9b0156d-7969-4176-aa12-f2047f4ab058', variable: 'pipeline')]) {
                //         sh 'echo "Password is $PASSWORD"'}
            }
        }
        stage( "Build" )
        {
            steps
            {
                // sh ' mv /var/lib/jenkins/workspace/Docker_practice_2/* /home/Docker ' 
                sh ' docker build -t imagejav /var/lib/jenkins/workspace/Docker_practice_2/Docker_Practice_2 '
                // sh ' docker build -t imagejav . '
            }
        }
        stage( "Run" )
        {
            steps
            {
                sh ' docker run -it imagejav '
            }
        }
    }

    post {
        success {
            // Do something on successful build
            echo 'Build successful!'
        }
        failure {
            // Do something on build failure
            echo 'Build failed!'
        }
    }
}
