pipeline {
	agent any
	
	stages {
		stage("Build") {
			steps {
				echo '---Build started----!'
				git 'https://github.com/jeydevops/Hello-java.git'
				sh 'mvn clean package -DskipTests=true'
				sh 'logstashSend'
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
		
	post
		{
		  logstashSend failBuild: true, maxLines: 1000
		}
	}
}
