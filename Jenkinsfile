pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean package'
            }
        }
        stage('Upload War To Nexus'){
            steps{
               nexusArtifactUploader artifacts: [
                   [
                       artifactId: 'simple-app',
                       classifier: '', 
                       file: 'target/simple-app-3.0.0.war', 
                       type: 'war'
                ]
            ], 
            credentialsId: 'Nexus3', 
            groupId: 'in.javahome', 
            nexusUrl: '172.31.1.34', 
            nexusVersion: 'nexus3', 
            protocol: 'http', 
            repository: 'my-simple-devop-app-release', 
            version: '3.0.0'
            }
        }
    }
}
