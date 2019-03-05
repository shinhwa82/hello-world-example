pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Build') {
      steps {
        withMaven(maven: 'M3') {
          sh 'mvn clean install'
        }

      }
    }
    stage('Results') {
      steps {
        realtimeJUnit(testResults: '**/target/surefire-reports/TEST-*.xml')
        archiveArtifacts 'target/*.jar'
      }
    }
  }
}