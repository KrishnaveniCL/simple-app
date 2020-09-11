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
                script
				{
                    nexusArtifactUploader artifacts: [
                        [
						    artifactId: 'simple-app',
							classifier: '',
							file: 'target/simple-app-3.0.0.war', 
							type: 'war'
						]
                    ], 
					credentialsId: 'Nexus', 
					groupId: 'in.javahome', 
					nexusUrl: '65.0.4.153:8081', 
					nexusVersion: 'nexus3', 
					protocol: 'http', 
					repository: 'nexus', 
					version: '3.0.0'
                    
                }
            }
        }
    }
}
