//DECLARITIVE
pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				echo "Build"
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
	}
}
