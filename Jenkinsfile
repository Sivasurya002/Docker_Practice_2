pipeline
{
    agent any
    stages
    {
        stage( "Clone" )
        {
            steps
            {
                sh ' rm -rf /var/lib/jenkins/workspace/Docker_practice_2/* '
                sh ' docker stop $(docker ps -a -q) '
                sh ' docker rm $(docker ps -a -q) '
                sh ' docker rmi $(docker images -q) '
                sh ' git clone https://github.com/Sivasurya002/Docker_Practice_2.git '
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
}
