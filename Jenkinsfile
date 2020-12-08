

pipeline {
	agent any
	
	stages{
		stage('checkout'){
			steps{
				echo 'checkout stage'
				git 'https://github.com/devopss1/demo.git'
			}
		}
		stage('Build'){
			steps{
				echo 'Build stage'
				sh '/root/opt/maven/bin/mvn package -f /home/tomcat/.jenkins/workspace/project2/sample/pom.xml'
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
s
q
				nexusArtifactUploader artifacts: [[artifactId: 'sample', classifier: '', file: '/home/tomcat/.jenkins/workspace/project2/sample/target/sample-1.1-SNAPSHOT.jar', type: 'jar']], credentialsId: '0e4de5af-4845-4e46-835b-d521bb9c223c', groupId: 'com.my', nexusUrl: '192.168.110.133:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'snapshots', version: '1.1-SNAPSHOT'
	    
			}
		}
		stage('Deploy'){
			steps{
				echo 'Deploy stage'
				sh 'cp /home/tomcat/.jenkins/workspace/project2/sample/target/sample-1.1-SNAPSHOT.jar  /root/opt/tomcat/webapps/'
			}
		}
	
	}
}
