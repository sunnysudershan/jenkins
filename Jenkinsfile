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
            - name: my-dockerhub-secret
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
                            repository: 'demo-2/my-app',
                            scanTimeout: 10,
                            standaloneScanner: true,
                            scanLayers: true,
                            tag: '1.0'
                        )
                    }
                }
            }
        }
    }
}
