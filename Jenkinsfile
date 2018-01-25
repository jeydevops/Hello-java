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
			parallel {
				stage("Unit Tests") {					
					steps {
						 echo 'Unit Tests Are Awesome!'
					}
				}
				stage("Integration Tests") {					
					steps {
						sh 'Integration Tests Are Awesome!'
					}
				}
				stage("Smoke Tests") {
					steps {
						sh 'Where There is Smoke there is Fire!!!'
					}
				}
			}
		}
		
		stage("Deploy") {
			steps {
				echo "Deploy!"
			}
		}
	}
}
