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
	// agent { docker { image 'maven:3.6.3'} }
	// agent { docker { image 'node:current-alpine3.11'} }
	environment {
		dockerHome = tool 'myDocker'
		movenHome = tool 'myMoven'
		PATH = "$dockerHome/bin:$movenHome/bin:$PATH"
	}
	stages {
		stage("Build"){
			steps{
				sh "moven --version"
				sh "docker --version"
				// sh "node --version"
				echo "Build"
				echo "PATH -$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
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
		stage("Build Docker Image"){
			steps{
				//"docker build -t ravindrahbtik11/hello-world-aspnetcore:$env.BUILD_TAG" 
				script{
					dockerImage = docker.build("ravindrahbtik11/hello-world-aspnetcore:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push docker Image'){
			steps{
				script{
					docker.withRegistory('', 'dockerhub'){
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
			}
		}

		stage('Package'){
			steps{
				sh "mv package -DskipTests"
			}
		}
	} 
	post{
		always{
			echo "I am awsome. I run always"
		}
		success{
			echo "I run always when you are successful"
		}

		failure{
			echo "I run when you are failure"
		}
		changed{
				echo "I run when you are changed"
		}
	}
}


