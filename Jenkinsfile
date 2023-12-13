node {

   // luc-app/ : nom du projet dans HARBOR
   def registryProjet='luc-app/'

   // ${version} : nom du parametre dans jenkins
   def IMAGE="${registryProjet}app:${version}"

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
       // harbor_id_luc : création d'un « credentials »
       docker.withRegistry('https://registry.ludovic.io/' , 'harbor_id_luc') {
              img.push 'latest'
              img.push()
          }
    }

}

