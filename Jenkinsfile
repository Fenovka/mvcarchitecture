pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'C:\\BuildTools\\nuget.exe restore Store.sln'
      }
    }

  }
}