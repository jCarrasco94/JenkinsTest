pipeline{
	agent any
	tools { 
		gradle 'gradle410'
	}
	stages{
		stage('Building'){
			steps{
				bat 'nuget restore JenkinsTest.sln'
				bat "\"${tool 'MSBuild'}\" JenkinsTest.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
			}
			post{
				success{
					 stash includes: 'release/distributions/*.nupkg', name: 'nupkg'
				}
			}
		}
	}
	post{
		always{
			deleteDir()
		}
	}
}