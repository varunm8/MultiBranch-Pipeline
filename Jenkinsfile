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
    }   
}
