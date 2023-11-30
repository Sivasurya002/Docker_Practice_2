pipeline
{
    agent any
    stages
    {
        stage( "Clone" )
        {
            steps
            {
                sh ' rm -rf * '
                sh ' sudo git clone https://github.com/Sivasurya002/Docker_Practice_2.git '
            }
        }
        stage( "Build" )
        {
            steps
            {
                sh ' sudo mv /var/lib/jenkins/workspace/Docker_practice_2/* /home/ec2-user/Docker ' 
                sh ' sudo docker build -t imagejav . '
            }
        }
        stage( "Run" )
        {
            steps
            {
                sh ' sudo docker run -it --name contjav imagejav '
            }
        }
    }
}
