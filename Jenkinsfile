pipeline {
	agent any
	
	stages {
		stage("Build") {
			steps {
				eho '---Build started----!'
				git 'https://github.com/jeydevops/Hello-java.git'
				sh 'mvn clean package -DskipTests=true'
				//logstashSend failBuild: true, maxLines: 1000
			}
		}
		
		stage("Testing") {							
			steps {
			 echo 'Unit Tests Are Awesome!'
			}
		}
		
		stage("Deploy") {
			steps {
				echo "Deploy!"
			}
		}
	}
		
		post{
		   always {
				echo '---Archive jenkins Console Logs to Elasticsearch----!'				
				logstashSend failBuild: true, maxLines: -1
			}
		    }	
}
