pipeline {
    agent {
          label 'windows'
    }
    stages {
         stage('Restore nuget') {
            steps {
                bat 'echo restoring...'
                //bat 'nuget restore HelloWorldDotnet.sln' // for .NET framework
            }
        }
        stage('Build') {
            steps {
                bat 'msbuild HelloWorldDotnet.sln /target:HelloWorldDotnet /p:Configuration=Release'
            }
        }
        stage('Test') {
            steps {
                //bat 'dotnet test --logger trx ./BigProject.NetCoreApp.Test/BigProject.NetCoreApp.Test.csproj'
                bat 'echo test'
            }         
        }
        
        stage('Deploy') {
            steps {
                archiveArtifacts artifacts: 'bin/Release/**', fingerprint: true
            }
        }
    }
}
