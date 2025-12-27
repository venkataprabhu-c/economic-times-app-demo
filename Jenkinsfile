pipeline{
	agent any
	{
		stages{
			stage("checkout"){
				sh "checkout SCM"
			}
			stage("Build"){
  sh "mvn clean package"
			}
			
			stage("test"){
  sh "mvn test"
			}
      
			
			stage("deploy"){
		
			}
			}
			}
