pipeline {
	agent any
    environment {
		//imagename = "chim3312/test-app-image"
		imagename = "192.168.1.5:30115/test-app-image"
        dockerImage = ''
        containerName = 'my-container'
        dockerHubCredentials = 'dockerhubadmin'
    }
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
					//docker buildx build --platform linux/arm/v7
                    app = docker.build("${imagename}:latest", "--network=host -f Dockerfile .")
                }
                sh 'ls -la'
			}
		}
		stage('Deploy') {
			steps {
				echo 'Deploying...'
				// Add your deployment commands here
				sh 'docker images'
				//sh 'docker tag test-app-image:0.7 http://192.168.1.115:5001/test-app-image:0.7'
				//sh 'docker push http://192.168.1.115:5001/test-app-image:0.7'
			}
		}
		stage('Deploy Image') {
			steps {
				script {
					//// Use Jenkins credentials for Docker Hub login
                    //withCredentials([usernamePassword(credentialsId: dockerHubCredentials, usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
					//	sh "docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD"
 
                      //  // Push the image
                       // sh "docker push ${imagename}:latest"
                       sh "docker push ${imagename}:latest"
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