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
	agent any
	stages('Build') {
		steps {
			echo "Build"
		}
	}
	stages('Test') {
		steps {
			echo "Test"
		}
	}
}
