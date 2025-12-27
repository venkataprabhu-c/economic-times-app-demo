pipeline {
    agent { label 'java' }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'mvn install'
            }
        }
         stage('Deploy to Tomcat') {
      steps {
			// sh "sudo rm -rf /opt/tomcat10/webapps/news-app"
			//sudo rm /opt/tomcat10/webapps/news-app.war
	sh "sudo cp /home/slave/workspace/test1/target/economic-times-app.war /opt/tomcat10/webapps"
		 
		
		  		  	sh "sudo /opt/tomcat10/bin/shutdown.sh"
			sh "sudo /opt/tomcat10/bin/startup.sh"
        }
      }
    }
}
