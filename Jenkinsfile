pipeline {
  agent any
  environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-sum-creds')
	}
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t sumayya2100/ss-app-be:v0.0.01 .'
      }
    }
    stage('Login') {
      steps {
      sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		stage('Push') {
			steps {
				sh 'docker push sumayya2100/ss-app-be:v0.0.01'
			}
		}
	}
	post {
		always {
			sh 'docker logout'
		}
	}

}
