node
{

def mavenHome = tool name: 'maven3.6.3'

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '4', daysToKeepStr: '', numToKeepStr: '4')), pipelineTriggers([pollSCM('* * * * *')])])

stage ("Get the code from GitHub")
{
git branch: 'development', credentialsId: '9dc2a2f2-3bff-4d5f-8e7f-fa7a76a7152f', url: 'https://github.com/kakshapanchal/maven-web-application.git'
}

stage ("Build the package")
{
sh "${mavenHome}/bin/mvn clean package"
}

/*
stage ("Generate the SonarQube Report")
{
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage ("Copy the artifact into Nexus Repository")
{
sh "${mavenHome}/bin/mvn deploy"
}

stage ("Deploy the application into Tomcat Server")
{
sshagent(['6e035e1d-d1e1-4fc0-935b-8ddb6e1967db']) {
    sh 'scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@65.2.187.195:/opt/apache-tomcat-9.0.65/webapps'
}
}

stage ("Send Email Notification")
{
emailext body: '''Build Over....

Thanks
''', subject: 'Build Over....', to: 'vivaanpanchal2615@gmail.com'
}

*/

}
