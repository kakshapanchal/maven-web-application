node
{

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '3', daysToKeepStr: '', numToKeepStr: '3')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

def mavenHome = tool name: "maven3.6.3"

stage ("Get the code from GitHub")
{
git branch: 'development', credentialsId: '11707efe-49f2-4438-854e-2c390cff0a6b', url: 'https://github.com/kakshapanchal/maven-web-application.git'
}

stage ("Build the package")
{
sh "${mavenHome}/bin/mvn clean package"
}

stage ("Generate SonarQube Report")
{
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage ("Upload artifact into Nexus Repo")
{
sh "${mavenHome}/bin/mvn deploy"
}

stage ("Deploy the application into Tomcat Server"){
sshagent(['6ef5e113-ec95-48c9-8a66-a1203cde1df3']) {
sh 'scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.110.161.39:/opt/apache-tomcat-9.0.65/webapps'
}
}

stage ("Send mail notification")
{
emailext body: '''Build Over...

Thanks
Santosh Panchal''', subject: 'Build Over....', to: 'panchal.santosh1986@gmail.com'
}

}
