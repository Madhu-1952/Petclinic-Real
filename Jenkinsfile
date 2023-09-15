pipeline{
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven'
    }
    stages{
        stage ('clean Workspace'){
            steps{
                cleanWs()
            }
        }
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
        stage ('maven Test') {
            steps {
                sh 'mvn test'
            }
        }
   }
}
