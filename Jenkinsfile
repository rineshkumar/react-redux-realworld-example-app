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
}
