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
		stage("Docker Build & Push"){
            steps{
                script{
                   withDockerRegistry(credentialsId: 'Docker', toolName: 'docker'){   
                       sh "docker build -t petclinic1 ."
                       sh "docker tag petclinic1 laddu11/petclinic1:latest "
                       sh "docker push laddu11/petclinic1:latest "
                    }
                }
            }
        }
   }
}
