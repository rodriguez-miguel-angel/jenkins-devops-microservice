// SCRIPTED PIPELINES. OLD APPROACH.

// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Integration Test') {
// 		echo "Integration git stTest"
// 	}
// }

// DECLARATIVE PIPELINES. NEWER APPROACH.
pipeline {
	// version-01:
	agent any
	// version-02:
	// agent {
		// docker {
			// version-a:
			// image 'maven:3.6.3'
			// version-b:
			// image 'node:13.8'
		// }
	// }
	environment {
		dockerHome = tool 'Udemy-Docker'
		mavenHome = tool 'Udemy-Maven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				sh 'docker version'
				// version-a:
				sh 'mvn --version'
				// version-b:
				// sh 'node --version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
				sh "mvn test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
				sh "mvn failsafe:integration-test failsafe:verify"
			}	
		}
		stage('Package') {
			steps {
				echo "Create jar file"
				sh "mvn package -DskipTests"
			}	
		}
		stage('Build Docker Image') {
			steps {
				// version-a: declarative version.
				// "docker build -t redscare/currency-exchange-devops:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("redscare/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push Docker Image') {
			steps {
				script {
					// version-01:
					docker.withRegistry('', 'dockerhub') {
						dockerImage.push();
						dockerImage.push('latest');
					}
					// version-02
					// docker.withDockerRegistry('', 'dockerhub') {
					// 	dockerImage.push();
					// 	dockerImage.push('latest');
					// }
				}
			}
		}
	} 
	
	post {
		always {
			echo "Soy chingon. This runs always."
		}
		success {
			echo "Soy chingon. This runs when the run is successful."
		}
		failure {
			echo "Soy chingon. This runs when the run fails."
		}
	}
	
}
