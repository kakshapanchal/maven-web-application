node {
    
def mavenHome = tool name: "maven3.6.3"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '3', daysToKeepStr: '', numToKeepStr: '3')), pipelineTriggers([pollSCM('* * * * * ')])])

stage ("Get the code from GitHub")
{
git branch: 'development', credentialsId: '4c1339a0-3bc5-409d-8ab9-aeb4d72ba948', url: 'https://github.com/kakshapanchal/maven-web-application.git'
}

stage ("Build the package")
{
sh "${mavenHome}/bin/mvn clean package"
}


/*
stage ("Generate SonarQube Report")
{
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage ("Upload artifact into Nexus repository")
{
sh "${mavenHome}/bin/mvn deploy"
}

stage ("Deploy the application to Tomcat Server")
{
sshagent(['ec056878-0d0f-4ccd-9e1a-a87442836243']) {
sh 'scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@65.1.133.206:/opt/apache-tomcat-9.0.64/webapps/'
}
}

stage ("Send mail notification")
{
emailext body: '''Build Over ....

Thanks
''', subject: 'Build Over.....', to: 'kakshapanchal.2288@gmail.com'
}
*/
}
