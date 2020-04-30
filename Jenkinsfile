pipeline {
  agent any
  stages {
    stage('Restore Nuget Packages') {
      steps {
        bat 'C:\\BuildTools\\nuget.exe restore Store.sln'
      }
    }

    stage('Build') {
      steps {
        bat 'C:\\BuildTools\\MSBuild\\14.0\\Bin\\MSBuild.exe Store.sln /p:Configuration=Release /p:PublishProfile=LocalPublishProfile'
      }
    }

    stage('Artifact Copy') {
      steps {
        archiveArtifacts(artifacts: 'Store.Web/bin/Release/Publish', allowEmptyArchive: true)
      }
    }

  }
}