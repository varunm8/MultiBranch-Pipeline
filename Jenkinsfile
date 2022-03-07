node {
    stage('continuousDownload')
    {
        git 'https://github.com/MRaju2022/maven.git'
    }
    stage('continuousBuild')
    {
        sh 'mvn package'
    }
  
}
