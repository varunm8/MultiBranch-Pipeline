node 
{
    stage('ContinuousDownload') 
    {
       git 'https://github.com/MRaju2022/maven.git'
    }
    stage('ContinuousBuild') 
    {
       sh 'mvn package'
    }
     stage('ContinuousDeployment') 
    {
      sh 'scp /home/ubuntu/.jenkins/workspace/scriptedPipeline/webapp/target/webapp.war  ubuntu@172.31.7.171:/var/lib/tomcat9/webapps/testenv.war'
    }
     stage('ContinuousTesting') 
    {
       git 'https://github.com/MRaju2022/Testing.git'
       sh 'java -jar /home/ubuntu/.jenkins/workspace/scriptedPipeline/testing.jar'
    }
    stage('ContinuousDelivery') 
    {
       sh 'scp /home/ubuntu/.jenkins/workspace/scriptedPipeline/webapp/target/webapp.war  ubuntu@172.31.6.98:/var/lib/tomcat9/webapps/prodenv.war'
    }
    
}
