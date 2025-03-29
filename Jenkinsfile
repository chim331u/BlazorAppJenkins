pipeline {
	agent any

	stages {
		stage('Checkout') {
			steps {
				echo 'Checking out code...'
				// Add your checkout commands here
				checkout scm
				sh 'ls -ls'
			}
		}
		stage('Build') {
			steps {
				echo 'Building...'
				// Add your build commands here
			}
		}
		stage('Deploy') {
			steps {
				echo 'Deploying...'
				// Add your deployment commands here
			}
		}
	}

	post {
		always {
			echo 'Cleaning up...'
			// Add cleanup commands here
		}
	}
}