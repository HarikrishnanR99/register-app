pipeline {
    agent { label "jenkinsagent" }
    tools {
	    jdk 'Java17'
	    maven 'harimaven'
    }
    environment {
	    APP_NAME = "register-app-pipeline"
	    RELEASE = "1.0.0"
	    DOCKER_USER ="thoratsunil121"
	    DOCKER_PASS ="dockerhub"
	    IMAGE_NAME = "${DOCKER_USER}" + "/" + "${APP_NAME}"
	    IMAGE_TAG = "${RELEASE}-${BUILD_NUMBER}"
	    JENKINS_API_TOKEN = credentials("JENKINS_API_TOKEN")
    }
    stages {
         stage("Cleanup Workspace"){
		 steps{
               	 cleanWs()
		 }
	 }
	 stage("Checkout from SCM"){
		 steps {
		     git branch: 'master', credentialsId: 'gitHub', url: 'https://github.com/HarikrishnanR99/register-app.git'
		 }
	 }
	 stage("Build Application"){
	     steps {
		 sh "mvn clean package"
	     }
          }
	 stage("Test Application"){
	      steps {
	            sh "mvn test"
              }
	  }
    }
}
