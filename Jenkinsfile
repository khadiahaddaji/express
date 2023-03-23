pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-app')
	}
	stages {
		stage('Build') {
			steps {
				sh 'docker build -t khaddaji/jenkins-app:latest .'
			}
		}
		stage('Login') {
			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		stage('Push') {
			steps {
				sh 'docker push khaddaji/jenkins-app:latest'
			}
		}
	}
	post {
		always {
			sh 'docker logout'
		}
	}
}
