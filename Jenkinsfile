pipeline {
    agent {
      kubernetes {
        yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: docker
            image: docker:dind
            command: ["/bin/sh", "-c"]
            args: ["dockerd & sleep infinity"]
            securityContext:
              privileged: true
              runAsUser: 0
          imagePullSecrets:
            - name: my-dockerhub-secret  // Change this to your local registry secret if needed
        '''
      }
    }
    stages {
        stage('docker pull') {
            steps {
                container('docker') {
                    script {
                        neuvector(
                            nameOfVulnerabilityToExemptFour: '',
                            nameOfVulnerabilityToExemptOne: '',
                            nameOfVulnerabilityToExemptThree: '',
                            nameOfVulnerabilityToExemptTwo: '',
                            nameOfVulnerabilityToFailFour: '',
                            nameOfVulnerabilityToFailOne: '',
                            nameOfVulnerabilityToFailThree: '',
                            nameOfVulnerabilityToFailTwo: '',
                            numberOfHighSeverityToFail: '0',
                            numberOfMediumSeverityToFail: '0',
                            controllerEndpointUrlSelection: 'NeuVector-Controller-1',
                            registrySelection: 'rmt',
                            repository: 'demo-2/my-app',  // Your application repository remains unchanged
                            scanTimeout: 10,
                            standaloneScanner: true,
                            tag: '1.0',
                            scannerImage: 'registry.aus.edu/neuvector/scanner:latest'  // Pull NeuVector scanner from your local registry
                        )
                    }
                }
            }
        }
    }
}
