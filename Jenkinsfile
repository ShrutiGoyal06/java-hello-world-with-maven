pipeline {
    agent any
		stages {
			stage('Build') { 
				steps {
					sh 'mvn clean package'
				}
			}
			stage('Uploading jar file to Artifactory') {
				steps {
					script{
					def server = Artifactory.server 'hmnoartifactorypro'
					def uploadSpec = """{
						"files": [
						{
						"pattern": "jb-hello-world-maven-0.1.0.jar",
                        			"target": "libs-snapshot-local/hmno/nsl/jar/"
						}
					]
				}"""
				server.upload(uploadSpec)
					}
			}
		}
	}
}
