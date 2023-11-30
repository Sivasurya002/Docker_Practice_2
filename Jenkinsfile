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
                    def containers = sh(script: ' docker ps -a -q ', returnStdout: true).trim()
                    if (containers) 
                    {
                        sh ' docker stop $containers '
                        sh ' docker rm $containers '
                    }
                    def images = sh(script: ' docker images -q ', returnStdout: true).trim()
                    if (images) 
                    {
                        sh ' docker rmi $images '
                    }
                    sh ' rm -rf /var/lib/jenkins/workspace/Docker_practice_2/* '
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
                sh ' docker run -d imagejav '
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
