pipeline {
	agent {
		docker {
			image 'node'
		}
	}
	environment {
		npm_config_cache = 'npm-cache'
	}
	stages {
		stage('Test') {
			steps {
				sh 'npm install'
			}
		}
		stage('Build') {
			steps {
				sh 'echo BUILDING PRODUCTION'
				timeout(time: 3, unit: 'MINUTES') {
					retry(3) {
						sh 'npm --version'
					}
				}
			}
		}
	}
	post {
		success {
			echo 'SUCCESSFULLY BUILDED THE SCRIPT'
		}
		failure {
			echo 'BUILDING FAILED'
		}
		changed {
			echo 'Jenkinsfile SCRIPT CHANGED'
		}
	}
}
