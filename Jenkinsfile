pipeline
{
    agent any
    
    stages
    {
        stage('ContinousDownload')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/varunm8/maven.git'
                    }
                    catch(Exception E)
                    {
                        mail bcc: '', body: 'Code Download from Git has failed', cc: '', from: '', replyTo: '', subject: 'Download Failure', to: 'gitadmin@gmail.com'
                    }
                }
                
            }
        }
        stage('ContinousBuild')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'mvn package'
                    }
                    catch(Exception E)
                    {
                        mail bcc: '', body: 'Build has failed', cc: '', from: '', replyTo: '', subject: 'Build Failure', to: 'DevTeam@gmail.com'
                    }
                }
            }
        }
        stage('ContinousDeploy')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'scp /home/ubuntu/.jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war ubuntu@172.31.6.24:/var/lib/tomcat9/webapps/TestEnv.war'
                    }
                    catch(Exception E)
                    {
                        mail bcc: '', body: 'Deployment to Testing Env has failed', cc: '', from: '', replyTo: '', subject: 'Deployment Failure', to: 'MiddleWare@gmail.com'
                    }
                }
            }
        }
        stage('ContinousTesting')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/varunm8/Testing.git'
                        sh 'java -jar /home/ubuntu/.jenkins/workspace/DeclarativePipeline/testing.jar'
                    }
                    catch(Exception E)
                    {
                        mail bcc: '', body: 'Testing has failed', cc: '', from: '', replyTo: '', subject: 'Testing Failure', to: 'TestingTeam@gmail.com'
                    }
                }
                
            }
        }
        stage('ContinousDelivery')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'scp /home/ubuntu/.jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war ubuntu@172.31.12.191:/var/lib/tomcat9/webapps/ProdEnv.war' 
                    }
                    catch(Exception E)
                    {
                        mail bcc: '', body: 'Deployment to Prodcution Env has failed', cc: '', from: '', replyTo: '', subject: 'Delivery Failure', to: 'ProdTeam@gmail.com'
                    }
                }
            }  
        }
    }
}
