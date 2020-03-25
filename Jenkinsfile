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
						echo "**/target/*.jar"
						
					def uploadSpec = """{
						"files": [
						{
						"pattern": "**/target/*.jar",
                        			"target": "libs-snapshot-local/hmno/nsl/jar/"
						}
					]
				}"""
				echo "pattern"
				server.upload(uploadSpec)
					}
			}
		}
	}
}
