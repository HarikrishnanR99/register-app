pipeline {
    agent { label "jenkinsagent" }
    tools {
        jdk 'java17'
        maven 'harimaven'
    }
    stages {
        stage("Cleanup Workspace") {
            steps {
                cleanWs()
            }
        }

 

        stage("Checkout from SCM") {
            steps {
                git branch: 'master', credentialsId: 'gitHub', url: 'https://github.com/HarikrishnanR99/register-app.git'
            }
        }

 

        stage("Build Application") {
            steps {
                sh "mvn clean package"
            }
        }

 

        stage("Test Application") {
            steps {
                sh "mvn test"
            }
        }
    }
}
