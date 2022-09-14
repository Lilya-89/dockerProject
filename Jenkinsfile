node{
  def registryProjet='registry.gitlab.com/lilya-89/jenkins-formation'
  def IMAGE="${registryProjet}:version-${env.BUILD_ID}"


    stage('Clone') {
        checkout scm
    }
	 def img = stage('Build') {
          docker.build("$IMAGE",  '.')
    }


      stage('Run') {
          img.withRun("--name run-$BUILD_ID -p 3000:80") { c ->
            sh 'docker ps'
            sh 'curl localhost:8080'
          }
    }


   stage('Push') {
          docker.withRegistry('https://registry.gitlab.com', 'gitLab') {
              img.push 'latest'
              img.push()
          }
    }

}
