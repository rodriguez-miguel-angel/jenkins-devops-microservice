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
