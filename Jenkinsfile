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
		stage{
			steps{
				sh 'docker build . -t javawebproject:${env.BUILD_ID}'
			}
		}
	}
}
