pipeline {
	agent any 
	parameters {
  choice choices: ['DEV', 'QA', 'UAT'], name: 'ENVIRONMENT'
}
        stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
		stage('Build') {
	           steps {
			  sh '/home/shruti/Documents/extract_files/apache-maven-3.9.6/bin/mvn install'
	                 }}
		stage('Deployment'){
		   steps {
		sh 'cp target/pipeline.war /home/shruti/Documents/extract_files/apache-tomcat-9.0.85/webapps'
			}}	
		stage ('slack-notification') {
		    steps {
	        slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '# devops', color: 'good', message: 'this is for test', teamDomain: 'student', tokenCredentialId: 'slack test'
		        }}   	
}}
