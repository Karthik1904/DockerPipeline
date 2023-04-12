podTemplate(
  containers: [
    containerTemplate(name: 'buildkit', image: 'moby/buildkit:master', ttyEnabled: true, privileged: true),
  ],
  volumes: []) {
    node(POD_LABEL) {
        stage('Checkout Code & Build Image') {  
            git branch: "master", url: "https://github.com/Karthik1904/DockerPipeline.git"
            container('buildkit') {
                NAME = "myapp"
                VERSION = "${env.BUILD_ID}"
                IMAGE = "${NAME}:${VERSION}"
                def C_DATE = new Date()
                echo "Running ${C_DATE.format("dd-MM-yyyy")}-build-${VERSION} on ${env.JENKINS_URL}"
              
                sh """ls"""
              
                def config = readYaml file: "deployment.azure.yaml"
                echo "Log ${config[0].spec.template.spec.containers[0].image}"
                writeYaml file: "deployment.azurem.yaml", data: config
              
                sh """cat deployment.azurem.yaml"""
            }
        }
    }
}
