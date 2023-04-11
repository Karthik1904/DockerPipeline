podTemplate(
  containers: [
    containerTemplate(name: 'buildkit', image: 'moby/buildkit:master', ttyEnabled: true, privileged: true),
  ],
  volumes: []) {
    node(POD_LABEL) {
        stage('Checkout Code & Build Image') {  
            NAME = "myapp"
            current_date_time=$(date)
            VERSION = "${env.BUILD_ID}-${env.GIT_COMMIT}"
            IMAGE = "${NAME}:${VERSION}"
            echo "Running current_date_time-${VERSION} on ${env.JENKINS_URL}"
        }
    }
}
