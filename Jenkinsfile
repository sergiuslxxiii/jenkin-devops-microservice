//SCRIPTED

//DECLARATIVE
pipeline{
	
	agent any
	//agent { docker { image 'node:13.8'} }
	//agent { docker { image 'maven:3.6.3'} }
	stages {
		stage('Build') {
			steps {
				//sh 'mvn --version'
				//sh 'node --version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
				echo "JENKINS_HOME - $env.JENKINS_HOME"
				echo "WORKSPACE - $env.WORKSPACE"	
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
			}
		}	
	}

	post{
		always{
			echo 'Im awesome. I run always'		
		}
		success{
			echo 'I run when you are sucessful'		
		}
		failure{
			echo 'I run when you fail'		
		}
	}	

}