pipeline {
	agent{docker{image 'node:14-alpine'}}
	environment{
		CONNECTION_STRING="ConnectionString"
		HelloWorldId=credentials("HelloWorldId")
	}
	stages{
		stage('build'){
			steps{
				retry(3){
					sh './HelloWorld.sh'
				}
				timeout(time : 3, unit : 'SECONDS'){
					sh './HelloWorld.sh'
				}
				echo "Connections string from environment ${env.CONNECTION_STRING}"
				//Jenkins variables 
				echo "BUILD_ID ${env.BUILD_ID}"
				echo "BUILD_NUMBER ${env.BUILD_NUMBER}"
				echo "BUILD_TAG ${env.BUILD_TAG}"
				echo "BUILD_URL ${env.BUILD_URL}"
				echo "EXECUTOR_NUMBER ${env.EXECUTOR_NUMBER}"
				echo "JAVA_HOME ${env.JAVA_HOME}"
				echo "JENKINS_URL ${env.JENKINS_URL}"
				echo "JOB_NAME ${env.JOB_NAME}"
				echo "NODE_NAME ${env.NODE_NAME}"
				echo "WORKSPACE ${env.WORKSPACE}"
				echo "Reading jenkins credentials 
				echo "HelloWorldId ${HelloWorldId}"
			}
		}
	}
	post {
		success{
			echo "Build succeeded "
		}
		failure{
			echo "Build failed"
		}
		unstable{
			echo "Build is unstable"
		}
		changed{
			echo "Build status has changed"
		}
	}
}
