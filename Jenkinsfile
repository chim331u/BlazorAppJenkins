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
				    script {
                    app = docker.build("test-app-image:0.1", "--network=host -f Dockerfile .")
                }
                sh 'ls -la'
			}
		}
		stage('Deploy') {
			steps {
				echo 'Deploying...'
				// Add your deployment commands here
			}
		}
		stage('RUN') {
			steps{
				echo "RUN..."
                script {
					try {
						sh "docker run --name test-app-jenkins --network=host imagename test-app-image:0.1 -p 8090:8080 "
                    } catch(err) {
						throw err
                    } finally {
					}
                }
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