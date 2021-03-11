pipeline {
	agent{docker{image 'node:14-alpine'}}
	environment{
		CONNECTION_STRING="ConnectionString"
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
