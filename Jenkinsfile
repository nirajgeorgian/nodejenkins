pipeline {
	agent {
		docker {
			image 'node'
		}
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
						sh 'node index.js'
					}
				}
			}
		}
	}
}
