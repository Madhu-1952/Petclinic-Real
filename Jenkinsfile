pipeline{
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven'
		SCANNER_HOME=tool 'sonar-scanner'
    }
    stages{
        stage ('checkout scm') {
            steps {
                git branch: 'main', credentialsId: 'github-creds', url: 'https://github.com/Madhu-1952/Petclinic-Real.git'
            }
        }
        stage ('maven compile') {
            steps {
                sh 'mvn clean compile'
            }
        }
		stage("Sonarqube Analysis "){
            steps{
				withSonarQubeEnv('sonar-server'){
				sh "${SCANNER_HOME}/bin/sonar-scanner"
				}
			}
		}
   }
}
