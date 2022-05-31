//DECLARITIVE
pipeline {
	agent any
	// agent { docker { image 'maven:3.6.3'} }
	// agent { docker { image 'node:13.8' } }
	environment {
		dockerHome = tool 'MyDocker'
		mavenHome = tool 'MyMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				//sh 'node --version'
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "$PATH"
				echo "BUILD_NUMBER  - $env.BUILD_NUMBER"
				echo "BUILD_ID  - $env.BUILD_ID"
				echo "JOB_NAME  - $env.JOB_NAME"
				echo "BUILD_TAG  - $env.BUILD_TAG"
			}
		} 

		stage('Build') {
			steps{
				sh "mvn clean compile"
			}
		}

		stage('Test') {
			steps {
				sh "mvn test"
			}
		}

		stage('Integration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}

		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}
		}

		stage("Build Docker Image") {
			steps {
				//"docker build -t gleask/currency-exchange:$env.BUILD_TAG"
				script{
					dockerImage = docker.build("gleask/currency-exchange:${env.BUILD_TAG}")
				}
			}
		}

		stage("Push Docker Image") {
			steps {
				script {
					docker.withRegistry('', 'DockerHub') {
						dockerImage.push() ;
						dockerImage.push('latest') ;
					}
				}
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
