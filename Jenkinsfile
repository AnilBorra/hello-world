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
		
	    
	}
}
