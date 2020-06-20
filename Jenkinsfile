//SCRIPTED

//DECLARATIVE
pipeline{

	agent any
	stages{
		stage('Build') {
			stages{
				echo 'Build'
			}
		}
		stage('Test') {
			stages{
				echo 'Test'
			}
		}
		stage('Integration Test') {
			stages{
				echo 'Integration Test'
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