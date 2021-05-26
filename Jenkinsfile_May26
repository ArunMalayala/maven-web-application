node
{

def mavenHome = tool name: "Maven3.8.1"

//properties([pipelineTriggers([pollSCM('* * * * *')])]) 

//properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])

	stage('CheckoutCode')
	{
	git branch: 'development', credentialsId: '71483e9d-7603-4392-92c1-75b8a448e05e', url: 'https://github.com/ArunMalayala/maven-web-application.git'
	}
	
	stage('Build')
	{
	sh "${mavenHome}/bin/mvn clean package"
	}
/*	
	stage('Execute SonarQube report')
	{
	sh "${mavenHome}/bin/mvn sonar:sonar"
	}
	
	stage('UploadArtifactsintoNexus')
	{
	sh "${mavenHome}/bin/mvn deploy"
	}
	
	stage('DeployAppintoTomcatServer')
	{
	sshagent(['c74a587e-3c1f-44ac-bd79-32483aea7da2']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@65.0.18.189:/opt/apache-tomcat-9.0.45/webapps"
		}
	}
	*/
	stage('SendEmailNotification')
	{
	emailext body: '''Build over....

	Regard,
	Arun.''', subject: 'Build over...', to: 'awsarun9@gmail.com'
	}
}
