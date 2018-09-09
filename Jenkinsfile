pipeline{
	agent any
	tools { 
		gradle 'gradle410'
	}
	stages{
		stage('Building'){
			steps{
				bat 'gradle msbuild --info'
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