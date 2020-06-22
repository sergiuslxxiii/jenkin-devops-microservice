//SCRIPTED

//DECLARATIVE
pipeline{
	
	agent any
	//agent { docker { image 'node:13.8'} }
	//agent { docker { image 'maven:3.6.3'} }

	environment{
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages {

		stage('Build') {
			steps {
				sh 'mvn --version'
				sh 'docker --version'
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
		
		stage('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}

		/*stage('Test') {
			steps {
				echo "mvn test"
			}
		}

		stage('Integration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}	*/

		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}
		}
		stage('Build Docker Image') {
			steps {
				//"docker build -t tadeus10/currency-exchange-devops:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("tadeus10/currency-exchange-devops:$env.BUILD_TAG") 
				}
			}
		}

		stage('Push Docker Image') {
			steps {				
				script {
					docker.withRegistry('','dockerhub')
					dockerImage.push();
					dockerImage.push('lastest');
				}
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