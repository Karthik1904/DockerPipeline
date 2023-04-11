podTemplate(
  containers: [
    containerTemplate(name: 'buildkit', image: 'moby/buildkit:master', ttyEnabled: true, privileged: true),
  ],
  volumes: []) {
    node(POD_LABEL) {
        stage('Checkout Code & Build Image') {  
            container('buildkit') {
                NAME = "myapp"
                VERSION = "${env.BUILD_ID}-${env.GIT_COMMIT}"
                IMAGE = "${NAME}:${VERSION}"
                echo "Running ${VERSION}-${sh date} on ${env.JENKINS_URL}"
            }
        }
    }
}
