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
	// agent any
	// version-02:
	agent {
		docker {
			// version-a:
			// image 'maven:3.6.3'
			// version-b:
			image 'node:13.8'
		}
	}
	stages {
		stage('Build') {
			steps {
				// version-a:
				// sh 'mvn --version'
				// version-b:
				sh 'node --version'
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
