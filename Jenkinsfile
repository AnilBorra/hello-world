pipeline{
	agent any
	tools {maven 'Maven 3.6.3'}
	stages
	{
		stage('Git Clone'){
			steps{
				git credentialsId: 'AnilBorra', url: 'https://github.com/AnilBorra/hello-world.git', branch: 'main'
			}
	 
	        }
		stage('Build Artifacts'){
			steps{
				sh 'mvn clean install'
			}
	 
	       }
		stage('Publish Artifacts'){
			steps{
				rtUpload (
					serverId: 'absoft_jfrog',
					spec: '''{
						"files": [
							{
								"pattern": "webapp/*.war",
								"target": "absoft_jfrog"
							}
						]
					}''',
					buildName: '${Build_Name}',
					buildNumber: '${Build_Number}'
				)
			}
	 
	    } 
		stage('Deploy Artifactory'){
			steps{
				sshagent(credentials: [''], ignoreMissing: true) {
					
  				  sh 'scp absoft_jfrog/webapp5.war http://54.165.1.188:8080/opt/apache-tomcat-9.0.43/webapps/'
				}
			}
		}
		
	    
	}
}
