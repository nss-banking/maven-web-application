node{

echo "The Job name is: ${env.JOB_NAME}"
echo "The build number is: ${env.BUILD_NUMBER}"
echo "The node name is:${env.NODE_NAME}"    
    
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])    

def mavenHome = tool name: 'maven3.8.8'

stage('CheckoutCode'){
git branch: 'development', credentialsId: 'ed95ce33-e3b8-48b2-8216-54e5ef37c017', url: 'https://github.com/nss-banking/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*  
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}
stage('UploadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn deploy"
}
stage('DeployeApplicationIntoTomcat'){
sshagent(['d2ac2f05-7abc-46a7-9294-812b1918b61f']) {
   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.3.0:/opt/apache-tomcat-9.0.73/webapps/"
 
}
}
*/
}
