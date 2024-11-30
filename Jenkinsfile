node {
 	def app
 	stage('Clone repository') {
 		git url: 'https://github.com/Sena-Han/OSS-J00.git', branch: 'main'
 	}
 	stage('Build image') {
		app = docker.build("sencream/test")
	}
	stage('Push image') {
		docker.withRegistry('https://registry.hub.docker.com', 'sencream') {
			app.push("${env.BUILD_NUMBER}")
			app.push("latest")
		}
	}
}
