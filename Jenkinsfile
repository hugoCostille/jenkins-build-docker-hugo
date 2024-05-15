node {

   def registryProjet='buildhugo/'
   def IMAGE="${registryProjet}app:3"

    stage('Clone') {
          checkout scm
    }

    def img = stage('Build') {
          docker.build("$IMAGE",  '.')
          }

    stage('Run') {
          img.withRun("--name run-$BUILD_ID") { c ->
       
          }
    }

    stage('Push') {
       docker.withRegistry('https://registry.ludovic.io/' , 'd8c4ec2a-b4cb-41bb-885e-e6e8b8d6f3c9') {
              img.push 'latest'
              img.push()
          }
    }
   stage('compuse_up') {
       sh 'docker compose up --detach'   
    }

}
