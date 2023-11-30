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
                sh ' sudo docker build -t imagejav /var/lib/jenkins/workspace/Docker_practice_2 '
            }
        }
        stage( "Run" )
        {
            steps
            {
                sh ' sudo docker run -it -d imagejav '
            }
        }
    }
}
