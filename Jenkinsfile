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
          sh '_JAVA_OPTIONS=-Djdk.net.URLClassPath.disableClassPathURLCheck=true mvn clean install'
        }
        
      }
    }
    stage('Results') {
      steps {
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts 'target/*.jar'
      }
    }
  }
}
