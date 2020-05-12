pipeline {
  agent any
  stages {
    stage('Restore Nuget') {
      steps {
        powershell 'nuget restore'
      }
    }

    stage('Build') {
      steps {
        powershell 'MSBuild Store.sln'
      }
    }

    stage('Deploy') {
      input {
        message 'Deploy to the master?'
        id 'Yes'
      }
      steps {
        powershell(script: '$env:deployMasterPassword', returnStdout: true)
      }
    }

  }
}