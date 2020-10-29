pipeline {
	node {
		agent any
		stages {
			stage("composer_install") {
				sh 'composer install'
			}
			stage('OWASP DependencyCheck') {
				steps {
					dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP Dependency-Check'
				}
			}
		}
		post {
			success {
				dependencyCheckPublisher pattern: 'dependency-check-report.xml'
			}
		}
	}
}
