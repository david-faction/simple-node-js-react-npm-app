pipeline {
	agent {
		docker {
			image 'node:6-alpine'
			args '-p 3000:3000'
		}
	}
	environment {
		CI = 'true'
	}
	stages {
		// stage('Build') {
		// 	steps {
		// 		sh 'npm install'
		// 	}
		// }
		stage('Update Yaml') {
			steps {
				script {
					def filename = 'test.yaml'
					def data = readYaml file: filename
					def newPropertyValue = 'updated value'

					// Update hash
					data.versions['app-ccv'] = newPropertyValue

					sh "rm $filename"
					writeYaml file: filename, data: data

					sh 'cat test.yaml'

					sh 'git status'
				}
			}
		}
		// stage('Test') {
		// 	steps {
		// 		sh './jenkins/scripts/test.sh'
		// 	}
		// }
		// stage('Deliver') {
		// 	steps {
		// 		sh './jenkins/scripts/deliver.sh'
		// 		input message: 'Finished using the web site? (Click "Proceed" to continue'
		// 		sh './jenkins/scripts/kill.sh'
		// 	}
		// }
	}
}