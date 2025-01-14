pipeline {
  agent any
  stages {
    stage('Pre Scan') { 
      steps {
        echo 'Pre Scan commands ...'
      }
    }
    stage('Check Image Pull') {
      steps {
        script {
          try {
            // Try to pull the image from the registry
            sh 'docker pull registry.aus.edu/demo-2/my-app:1.0'
            echo 'Image successfully pulled!'
          } catch (Exception e) {
            echo 'Failed to pull the image!'
            error 'Image pull failed. Exiting pipeline.'
          }
        }
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
          numberOfHighSeverityToFail: '', 
          numberOfMediumSeverityToFail: '', 
          registrySelection: 'rmt', 
          repository: 'registry.aus.edu/demo-2/my-app:1.0', 
          scanLayers: true, 
          scanTimeout: 10, 
          tag: 'latest'
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
