node
{
    stage('ContinuousDownload') 
    {
        git 'https://github.com/varunm8/maven.git'   
    }
    stage('ContinuousBuild') 
    {
        sh 'mvn package'
    }
    stage('ContinuousDeploy') 
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war  ubuntu@172.31.6.24:/var/lib/tomcat9/webapps/Test.war'
    }
    stage('ContinuousTesting') 
    {
        git 'https://github.com/varunm8/Testing.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
  stage('ContinuousDelivery') 
    {
       sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war  ubuntu@172.31.12.191:/var/lib/tomcat9/webapps/Prod.war'
    }
}

