pipeline{
	agent any
	stages{
		stage('Build Application'){
			steps{
				sh 'mvn clean package'
			}
			post{
				success{
					echo 'Now archiving the Artifacts...'
					archiveArtifacts artifacts: '**/*.war'
				}
			}		
		}
		stage('Deploy in Staging Environment'){
			steps{
				build job: 'java-web-project-stag_1'
			}
		}
		stage('Deploy in Production Environment'){
			steps{
				build job: 'java-web-project-prod_1'
			}
		}
	}
}
