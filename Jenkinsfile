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
				sh 'docker images'
				// Add your build commands here
				    script {
                    app = docker.build("test-app-image:0.6", "--network=host -f Dockerfile .")
                }
                sh 'ls -la'
			}
		}
		stage('Deploy') {
			steps {
				echo 'Deploying...'
				// Add your deployment commands here
				sh 'docker images'
				sh 'docker tag test-app-image:0.6 http://192.168.1.115:5001/test-app-image:latest'
				sh 'docker push http://192.168.1.115:5001/test-app-image:latest'
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