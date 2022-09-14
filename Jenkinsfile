node{
  def app

    stage('Clone') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("ilyas/nginx")
    }

    stage('Test image') {
        docker.image('ilyas/nginx').withRun('-p 3030:3030') { c ->
        sh 'docker ps'
        sh 'curl http://localhost:80'
	     }
    }
}
