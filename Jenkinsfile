//DECLARITIVE
pipeline {
	// agent any
	agent {
		docker {
			{
				image 'maven:3.6.3'
			}
		}
	}
	stages {
		stage('Build') {
			steps {
				sh 'mvn --version'
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
		unstable {
			echo 'I Run when Unstable'
		}
		changed {
			echo 'I Run when Code Changed'
		}
	}
	
	
}
