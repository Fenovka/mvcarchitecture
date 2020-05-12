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
        parameters {
          string(name: 'password', defaultValue: '', description: 'Password')
        }
      }
      steps {
        powershell 'echo "${params.password}"'
        powershell 'MSBuild Store.sln /p:DeployOnBuild=true /p:PublishProfile=Deploy_Master /p:Password="${params.password}"'
      }
    }

  }
}