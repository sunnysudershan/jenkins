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
        controllerEndpointUrlSelection: 'NeuVector-Controller-1',
        registrySelection: 'rmt',
        repository: "registry.aus.edu/demo-2/my-app",
        scanLayers: true, 
        tag: "1.0"
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
