//SCript

// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Integration Test') {
// 		echo "Test"
// 	}
// }

// node {
// 	echo "Build"
// 	echo "Test"
// 	echo "Test"
// }

// Declarative pipeline

pipeline{
	agent any
	stages {
		stage("Build"){
			steps{
				echo "Build"
			}
		}
		stage("Test"){
			steps{
				echo "Test"
			}
		}
		stage("Integration Test"){
			steps{
				echo "Integration Test"
			}
		}
	} post{
		always{
			echo "I am awsome. I run always"
		}
		success{
			echo "I run always when you are successful"
		}

		failure{
			echo "I run when you are failure"
		}
	}
}


