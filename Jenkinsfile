pipeline{
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven'
    }
    environment {
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
		stage ('Build and push to docker hub'){
            steps{
                script{
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
					    sh "docker login -u laddu11 -p madhu@1952"
                        sh "docker build -t petshop ."
                        sh "docker tag petshop manju/petshop:latest"
                        sh "docker push manju/petshop:latest"
                   }
                }
            }
        }
   }
}
