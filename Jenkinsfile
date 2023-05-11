podTemplate(
  containers: [
    containerTemplate(name: 'azcli', image: 'mcr.microsoft.com/azure-cli:latest', ttyEnabled: true, privileged: true)
  ],
  volumes: []) {
    node(POD_LABEL) {
        stage('Copy Build Image From QA to Prod ACR') {  
            container('azcli') {
                sh 'az login --service-principal -u 03eed3d9-9b2f-4d49-a7f3-c6dbcf4025e1 -p 5QU8Q~vE9Qsi7VFdfkHYStgnJ3f9yGGMbow3ycAF -t c4b27970-fe8c-49c3-993b-07efb3307e33'
                sh 'az acr import --name proodacr --source qaacr.azurecr.io/proj/uat/deploycheck:10-05-23-build-1 --username qaacr --password X5P6hS7NAkuFaCDifPvPajpC+1D8mK4KsRdaKP9ccG+ACRBahtdw --image proj/prod/deploycheck:11-05-23-build-1'
            }
        }
    }
}
