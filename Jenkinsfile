node{
        def buildNumber = BUILD_NUMBER
	def Maven = tool name: "Maven"
	
	stage('Code Checkout'){
		git branch: 'main', 
		credentialsId: 'GitHub', 
		url: 'https://github.com/yog1995/Scotia_Demo.git'
	}
	stage('Maven Build'){
		sh "${Maven}/bin/mvn clean package"
	}
	stage('Deploying to Tomcat'){
		sshagent(['Tomcat']) {
   			sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@18.190.154.239:/opt/apache-tomcat-9.0.52/webapps/"
		}
	}
			
}
