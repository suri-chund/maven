node('master') 
{
   stage('Continuous Download') 
   {
      git 'https://github.com/suri-chund/maven.git'
   }
   stage('Continuous Build')
   {
       sh label: '', script: 'mvn package'
   }
   stage('ContinuousDeployment')
   {
       sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/A1/webapp/target/webapp.war ubuntu@172.31.19.160:/var/lib/tomcat8/webapps/t3app.war'
   }
   stage('Continuous Testing')
   {
       git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
   
       sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/A1/testing.jar'
       
   }
   stage('Continuous Delivery')
   {
       input message: 'Wating for Approval from the DM!', submitter: 'srinivas'
       
       sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/A1/webapp/target/webapp.war ubuntu@172.31.27.95:/var/lib/tomcat8/webapps/p3app.war'
   }
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
}
