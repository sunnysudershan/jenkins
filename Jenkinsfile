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
        neuvector nameOfVulnerabilityToExemptFour: '',
        nameOfVulnerabilityToExemptOne: '', 
        nameOfVulnerabilityToExemptThree: '', 
        nameOfVulnerabilityToExemptTwo: '', 
        nameOfVulnerabilityToFailFour: '', 
        nameOfVulnerabilityToFailOne: '', 
        nameOfVulnerabilityToFailThree: '', 
        nameOfVulnerabilityToFailTwo: '', 
        numberOfHighSeverityToFail: '400', 
        numberOfMediumSeverityToFail: '400', 
        registrySelection: 'rmt',
        repository: "registry.aus.edu/demo-2/my-app",
        scanLayers: true, 
        tag: "2.0",
        controllerEndpointUrlSelection: "https://neuvector.aus.edu/"
      }  
    }
    stage('Build') { 
      steps {
        echo 'Build commands ...'
      }
    }
    stage('Deploy') { 
      steps {
        echo 'Deploy commands ...'
      }
    }
    stage('Test') { 
      steps {
        echo 'Test commands ...'
      }
    }
    stage('Release') { 
      steps {
        echo 'Release commands ...'
      }
    }    
  }
}
