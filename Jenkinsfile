node('built-in') 
{
    stage('continuousdownload')
    {
        git 'https://github.com/IntelliqDevops/maven.git'
    }
    stage('continuousbuild')
    {
        sh 'mvn package'
    }
    stage('continuousdeployment')
    {
     sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.23.20:/var/lib/tomcat10/webapps/test1.war'   
    }
    stage('continuoustesting')
    {
        git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline/testing.jar'
    }
    stage('continuousdelivery')
    {
        sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.25.127:/var/lib/tomcat10/webapps/prodapp' 
    }
}    
