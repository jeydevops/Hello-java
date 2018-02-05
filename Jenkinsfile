pipeline {
	agent any
	
	stages {
		stage("Build") {
			try
			{
			steps {
				echo '---Build started----!'
				git 'https://github.com/jeydevops/Hello-java.git'
				sh 'mvn clean pakage -DskipTests=true'
				//logstashSend failBuild: true, maxLines: 1000
			}
			}
			catch(err){
				echo '---FAILURE CATCH: Archive jenkins Console Logs to Elasticsearch----!'				
				logstashSend failBuild: true, maxLines: -1
				throw(err)
				
			}
			finally {
    			echo '---FAILURE FINALLY: Archive jenkins Console Logs to Elasticsearch----!'				
				logstashSend failBuild: true, maxLines: -1
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
		  // always {
		//		echo '---ALWAYS: Archive jenkins Console Logs to Elasticsearch----!'				
		//		logstashSend failBuild: true, maxLines: -1
		//	}
		  failure {
            			echo '---FAILURE: Archive jenkins Console Logs to Elasticsearch----!'				
				logstashSend failBuild: true, maxLines: -1
        		}
		    }	
}
