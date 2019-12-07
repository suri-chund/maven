node('master') 
{
   stage('ContinuousDownload') 
   {
      git 'https://github.com/intelliqittrainings/maven.git'
   }
   stage('ContinuousBuild')
   {
       sh label: '', script: 'mvn package'
   }
   stage('ContinuousDeployment')
   {
       sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.0.103:/var/lib/tomcat8/webapps/testapp.war'
   }
   stage('ContinuousTesting')
   {
       git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
   
       sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
       
   }
   stage('ContinuousDelivery')
   {
       input message: 'Wating for Approval from the DM!', submitter: 'srinivas'
       
       sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.10.26:/var/lib/tomcat8/webapps/prodapp.war'
   }
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
}
