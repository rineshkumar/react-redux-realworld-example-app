pipeline{
    environment{ 
		gitUrl="https://github.com/rineshkumar/react-redux-realworld-example-app.git"
        registry = "rineshkumar/expressapp" 
        registryCredential = 'dockerLogin'//credentials('dockerLogin')
        dockerImageName = "${registry}:${env.BUILD_ID}"
		
    }
    agent any 
    stages{
        stage('Cloning our Git') { 
            steps{ 
                git "${env.gitUrl}"
            }
        } 
        stage("Building our image"){ 
            steps{
                script{
                    dockerImage = docker.build "${env.dockerImageName}"
                }
            }
        }

        stage("Deploy our image"){
            steps{
                script{ 
                    docker.withRegistry( "", 'dockerLogin' ){
                        dockerImage.push() 
                    }
                }
            }
        }
        stage("Cleaning up"){
            steps{
                sh 'docker rmi ${env.dockerImageName}'
            }
        } 
    }
}