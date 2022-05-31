//DECLARITIVE
pipeline {
	agent any
	// agent { docker { image 'maven:3.6.3'} }
	// agent { docker { image 'node:13.8' } }

	stages {
		stage('Build') {
			steps {
				sh 'node --version'
				sh 'mvn --version'
				echo "Build"
				echo "$PATH"
				echo "BUILD_NUMBER  - $env.BUILD_NUMBER"
				echo "BUILD_ID  - $env.BUILD_ID"
				echo "JOB_NAME  - $env.JOB_NAME"
				echo "BUILD_TAG  - $env.BUILD_TAG"
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
	post {
		always {
			echo 'I Always Run'
		}
		success {
			echo 'I Run when Successful'
		}
		failure {
			echo 'I Run when Failure'
		}
		unstable {
			echo 'I Run when Unstable'
		}
		changed {
			echo 'I Run when Code Changed'
		}
	}
	
	
}
