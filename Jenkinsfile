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
	stages {
		stage('Build') {
			steps {
				//sh 'mvn --version'
				// sh 'node --version'
				echo "Build"
				echo "$PATH"
				echo "Build Number: $env.BUILD_NUMBER"
				echo "Build ID: $env.BUILD_ID"
				echo "Build Tag: $env.BUILD_TAG"
				
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
	}
}
