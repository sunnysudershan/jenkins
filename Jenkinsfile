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
        neuvector controllerEndpointUrlSelection: 'NeuVector-Controller-1',
                 nameOfVulnerabilityToExemptFour: '', 
                 nameOfVulnerabilityToExemptOne: '', 
                 nameOfVulnerabilityToExemptThree: '', 
                 nameOfVulnerabilityToExemptTwo: '', 
                 nameOfVulnerabilityToFailFour: '', 
                 nameOfVulnerabilityToFailOne: '', 
                 nameOfVulnerabilityToFailThree: '', 
                 nameOfVulnerabilityToFailTwo: '', 
                 numberOfHighSeverityToFail: '', 
                 numberOfMediumSeverityToFail: '', 
                 registrySelection: 'rmt', 
                 repository: 'demo-2/my-app:1.0', 
                 scanLayers: true, 
                 scanTimeout: 10, 
                 tag: 'latest'
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
