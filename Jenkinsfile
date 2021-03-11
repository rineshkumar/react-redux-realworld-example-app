pipeline{
	agent {
		docker {
			{ image 'node:14-alpine' }
		}
	}
	stages{
		Stage('build'){
			steps{
				sh '''
					npm --version
					echo "Hello World "
				'''
			}
		}
	}	
}
