node{

def mavenHome = tool name: "maven3.6.3"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '3', daysToKeepStr: '', numToKeepStr: '3')), pipelineTriggers([pollSCM('* * * * *')])])

stage ("Get the code from GitHub")
{
git branch: 'development', credentialsId: '8c07bbe8-fb6d-4afb-9660-0fc188c24f82', url: 'https://github.com/kakshapanchal/maven-web-application.git'
}

stage ("Build the package")
{
sh "${mavenHome}/bin/mvn clean package"
}

 /*
stage ("Generating SonarQube Report")
{
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage ("Upload the artifact into Nexus")
{
sh "${mavenHome}/bin/mvn deploy"
}

stage ("Deploy the application into Tomcat Server")
{
sshagent(['019ef681-151d-4e98-bdb5-9f60f140560f']) {
 sh 'scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.111.168.84:/opt/apache-tomcat-9.0.64/webapps'
}
}

stage ("Send email notification")
{
emailext body: '''Build Over ......

Thanks
Santosh Panchal''', subject: 'Build Over.....', to: 'kakshapanchal.2288@gmail.com'
}
*/
}
