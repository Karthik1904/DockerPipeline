podTemplate(
  containers: [
    containerTemplate(name: 'buildkit', image: 'moby/buildkit:master', ttyEnabled: true, privileged: true),
  ],
  volumes: []) {
    node(POD_LABEL) {
        environment { 
            NAME = "myapp"
            VERSION = "${env.BUILD_ID}-${env.GIT_COMMIT}"
            IMAGE = "${NAME}:${VERSION}"
        }
        stage('Checkout Code & Build Image') {  
            echo "Running ${VERSION} on ${env.JENKINS_URL}"
        }
    }
}
