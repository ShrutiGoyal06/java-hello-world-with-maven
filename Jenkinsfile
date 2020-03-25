pipeline {
    agent any
		stages {
			stage('Build') { 
				steps {
					sh 'mvn clean package'
				}
			}
			stage('Uploading jar file to Artifactory') {
				steps 
				{
					def server = Artifactory.server 'hmnoartifactorypro'
					def uploadSpec = """{
						"files": [
						{
						"pattern": "**/target/*.jar",
                        			"target": "libs-snapshot-local/hmno/nsl/jar/"
						}
					]
				}"""
				server.upload(uploadSpec)
				
			}
		}
	}
}
