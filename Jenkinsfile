podTemplate(
  containers: [
    containerTemplate(name: 'buildkit', image: 'moby/buildkit:master', ttyEnabled: true, privileged: true),
  ],
  volumes: []) {
    node(POD_LABEL) {
        stage('Checkout Code & Build Image') {  
            container('buildkit') {
                NAME = "myapp"
                VERSION = "${env.BUILD_ID}"
                IMAGE = "${NAME}:${VERSION}"
                def C_DATE = new Date()
                echo "Running ${C_DATE.format("dd-MM-yyyy")}-Build-${VERSION} on ${env.JENKINS_URL}"
            }
        }
    }
}
