// scripted
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Integration Test') {
// 		echo "Integration Test"
// 	}
// }

// declarative pipeline 
pipeline {
	// agent { docker { image 'node:latest'} }
	agent any 
	
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	
	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "$PATH"
				echo "Build Number: $env.BUILD_NUMBER"
				echo "Build ID: $env.BUILD_ID"
				echo "Build Tag: $env.BUILD_TAG"
				
			}
		}
		
		stage('Compile') {
			steps {
				echo "Compile"
				sh "mvn clean compile"
			}
		}
		
// 		stage('Test') {
// 			steps {
// 				echo "Test"
// 				sh "mvn test"
// 			}
// 		}
		
// 		stage('Int Test') {
// 			steps {
// 				echo "Int Test"
// 				sh "mvn failsafe:integration-test failsafe:verify"
// 			}
// 		}
		
		stage('Package') {
			steps {
				echo "Package"
				sh "mvn package -DskipTests"
			}
		}
		
		stage('Build Docker') {
			steps {
				echo "Build Docker"
				// "docker build -t jaywatson2pt0/currency-exchange-devops:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("jaywatson2pt0/currency-exchange-devops:${env.BUILD_TAG}");
				}
			}
		}
		
		stage('Push Docker') {
			steps {
				echo "Push Docker"
				script {
					docker.withRegistry('', 'dockerhub') {
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
			}
		}

	}
}
