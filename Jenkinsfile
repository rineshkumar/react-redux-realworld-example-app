pipeline {
	agent { docker { image 'node:14-alpine' } }
	stages{
		stage('build'){
			steps{
				retry(3){
					sh './HelloWorld.sh'
				}
				timeout(time : 3, unit : 'SECONDS'){
					sh './HelloWorld.sh'
				}
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
