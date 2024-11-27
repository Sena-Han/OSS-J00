node {
 	def app
 	stage('Clone repository') {
 		git 'https://github.com/Sena-Han/OSS-J00.git'
 	}
 	stage('Build image') {
		app = docker.build("sencream/test")
	}
 	stage('Test image') {
		app.inside {
			sh'make test'
 		}
	}
	stage('Push image') {
		docker.withRegistry('https://registry.hub.docker.com', 'sencream') {
			app.push("${env.BUILD_NUMBER}")
			app.push("latest")
		}
	}
}
