pipeline {
	agent any
	
	stages {
		stage("Build") {
			steps{
			script {
			try
			{
			
				eho '---Build started----!'
				//git 'https://github.com/jeydevops/Hello-java.git'
				sh 'mvn clean package -DskipTests=true'
				//logstashSend failBuild: true, maxLines: 1000			
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
			}
			
		}
		
		stage("Testing") {							
			steps {
				script {
			try
			{
			 echo 'Unit Tests Are Awesome!'
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
			}					
		}
		
		stage("Deploy") {
			steps {
				script {
			try
			{
				echo "Deploy!"
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
			}
	}
		
		post{
		  // always {
		//		echo '---ALWAYS: Archive jenkins Console Logs to Elasticsearch----!'				
		//		logstashSend failBuild: true, maxLines: -1
		//	}
		
		  failure {
			  script {
				try
		  		{
            			echo '---FAILURE: Archive jenkins Console Logs to Elasticsearch----!'				
				logstashSend failBuild: true, maxLines: -1
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
			}
		}	
}
