pipeline {
    agent any
    stages {
        stage('Pre Scan') { 
            steps {
                echo 'Pre Scan commands ...'
            }
        }
        
        stage('Image Scan') { 
            steps {
                container('docker') {
                    script {
                        // NeuVector scan for image
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
                            tag: '1.0',
                            scannerImage: 'registry.aus.edu/neuvector/scanner:latest'  // Use local scanner image
                        )
                    }
                }
            }
        }

        stage('Build') { 
            steps {
                echo 'Build commands ...'
                // Add build steps here
            }
        }

        stage('Deploy') { 
            steps {
                echo 'Deploy commands ...'
                // Add deploy steps here
            }
        }

        stage('Test') { 
            steps {
                echo 'Test commands ...'
                // Add test steps here
            }
        }

        stage('Release') { 
            steps {
                echo 'Release commands ...'
                // Add release steps here
            }
        }    
    }
}
