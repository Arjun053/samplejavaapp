pipeline {
  agent any

  tools{
    maven 'M3'
  }
  stages {
    stage('compile') {
      steps {
        git 'https://github.com/lerndevops/samplejavaapp.git'
        bat 'mvn compile'
        sleep 10
      }
    }

    stage('codereview-pmd') {
      
      steps {
        bat 'mvn -P metrics pmd:pmd'
      }
    }

    stage('unit-test') {
      post {
        success {
          junit 'target/surefire-reports/*.xml'
        }

      }
      steps {
        bat 'mvn test'
      }
    }

    stage('package') {
      steps {
        bat 'mvn clean package'
      }
    }

  }
}
