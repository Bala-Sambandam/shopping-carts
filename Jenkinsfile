pipeline {
  agent any
  stages {
    stage('build') {
      steps {
	echo 'Pipeline Status: Started'
        echo 'Build Status: Started'
        sh 'mvn compile'
	echo 'Build Status: Completed'
      }
    }

    stage('test') {
      steps {
        echo 'Test Status: Started'
        sh 'mvn test'
	echo 'Test Status: Completed'
     }
    }

    stage('package') {
      steps {
        echo 'Package Status: Started'
        sh 'mvn package -DskipTests'
	echo 'Package Status: Completed'
      }
    }

    stage('Artifact') {
      steps {
	echo 'Extracting Artifact'
        archiveArtifacts '**/target/*.jar'
	echo 'Extracted Artifact'
      }
    }

  }
  tools {
    maven 'maven'
  }
  post {
    always {
      echo 'Pipeline Status: Completed'
    }

  }
}
