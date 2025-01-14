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
        neuvector(
          nameOfVulnerabilityToExemptFour: '', 
          nameOfVulnerabilityToExemptOne: '', 
          nameOfVulnerabilityToExemptThree: '', 
          nameOfVulnerabilityToExemptTwo: '', 
          nameOfVulnerabilityToFailFour: '', 
          nameOfVulnerabilityToFailOne: '', 
          nameOfVulnerabilityToFailThree: '', 
          nameOfVulnerabilityToFailTwo: '', 
          numberOfHighSeverityToFail: '10', // Set appropriate threshold
          numberOfMediumSeverityToFail: '20', // Set appropriate threshold
          controllerEndpointUrlSelection: 'NeuVector-Controller-1',
          registrySelection: 'rmt',
          scanLayers: true, 
          scanTimeout: 10, 
          tag: '1.0'
        )
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
