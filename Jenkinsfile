pipeline{
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven'
    }
    stages{
        stage ('checkout scm') {
            steps {
                git branch: 'main', credentialsId: 'github-creds', url: 'https://github.com/Madhu-1952/Petclinic-Real.git'
            }
        }
		stage ('creating the build') {
			steps {
				sh "mvn clean package"
				
			}
		}
   }
}
