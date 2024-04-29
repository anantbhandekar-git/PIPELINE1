pipeline {
	agent any
	
	parameters {
  		string defaultValue: 'DEV', name: 'ENV'
	}
        triggers {
  		pollSCM '* * * * *'
	}
	stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
		stage('Build') {
	           steps {
			  sh '/home/anant/Downloads/apache-maven-3.9.6/bin/mvn install'
	                 }}
		stage('Deployment'){
		    steps {
			sh '''if [ $ENV = "DEV" ];then
 cp target/PIPELINE1.war  /home/anant/Downloads/apache-tomcat-9.0.88/webapps
elif [ $ENV = "QA" ];then
echo "invalid string"
fi'''
			
			}}
  stage("notification"){
  steps{
slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#anant1', color: 'good', message: 'welcome to jenkins', teamDomain: 'DEVOPS', tokenCredentialId: 'c02cb5a8-c731-4a70-afa5-19a5d5453918' 
}
}

	}}
