pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages{
        stage('Build'){
            steps {
                bat 'mvn -X clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
		stage('deploy to staging'){
			steps{
				build job: 'deploy-to-staging'
			}
		}
    }
}