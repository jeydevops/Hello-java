pipeline {
	agent any
	
	stages {
		stage("Build") {
			steps {
				echo '---Build started----!'
				git 'https://github.com/jeydevops/Hello-java.git'
				sh 'mvn clean package -DskipTests=true'
				//logstashSend 'failBuild: true, maxLines: 1000'
			}
		}
		
		stage("Testing") {			
							
					steps {
						 echo 'Unit Tests Are Awesome!'
					}
								
					steps {
						sh 'Integration Tests Are Awesome!'
					}
				
					steps {
						sh 'Where There is Smoke there is Fire!!!'
					}
				 parallel steps
			
		}
		
		stage("Deploy") {
			steps {
				echo "Deploy!"
			}
		}
	}
}
