pipeline {
	agent any
	stages {
		stage('init'){
			steps{
				sh "docker rm -f \$(docker ps -aq) || true"
				sh "docker rmi -f \$(docker images) || true"
			}
		}
		stage('build'){
			steps{
				sh "docker build -t node:${BUILD_NUMBER} ."
			}
		}
		stage('run'){
			steps{
				sh "docker run -d -p 80:5000 --name node node:${BUILD_NUMBER}"
			}
		}
	}
 }
