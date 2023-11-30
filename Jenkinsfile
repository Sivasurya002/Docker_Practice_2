pipeline
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
                sh ' sudo git clone -b python https://github.com/Sivasurya002/Docker_Practice_2.git '
            }
        }
        stage( "Build" )
        {
            steps
            {
                sh ' sudo mv /var/lib/jenkins/workspace/IMG/Docker-jenkins-tasks/* /home/ec2-user/Docker ' 
                sh ' sudo docker build -t imagejav . '
            }
        }
        stage( "Run" )
        {
            steps
            {
                sh ' sudo docker run -it imagejav '
            }
        }
    }
}