

pipeline {
	agent any
	
	stages{
		stage('checkout'){
			steps{
				echo 'checkout stage'
				git 'https://github.com/swathinattuva/1234.git'
			}
		}
		stage('Build'){
			steps{
				echo 'Build stage'
				sh '/root/opt/maven/bin/mvn package -f /home/tomcat/.jenkins/workspace/Project2/sample/pom.xml'
			}
		}
		stage('Test'){
			steps{
				echo 'Test stage'
			}
		}
		stage('Artifact upload'){
			steps{
				echo 'Artifact Upload stage'
				nexusArtifactUploader artifacts: [[artifactId: 'sample', classifier: '', file: '/home/tomcat/.jenkins/workspace/Project2/sample/target/sample-1.1-SNAPSHOT.jar', type: 'jar']], credentialsId: '18352780-27b9-497d-b4ee-921e5cacde3c', groupId: 'com.my', nexusUrl: '192.168.110.133:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'snapshots', version: '1.1-SNAPSHOT'
	    
			}
		}
		stage('Deploy'){
			steps{
				echo 'Deploy stage'
				sh 'cp /home/tomcat/.jenkins/workspace/Project2/sample/target/sample-1.1-SNAPSHOT.jar  /root/opt/tomcat/webapps/'
			}
		}
	
	}
}
