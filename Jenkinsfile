pipeline { 

    environment { 
		gitUrl="https://github.com/rineshkumar/react-redux-realworld-example-app.git"
        registry = "rineshkumar/expressapp" 
        registryCredential = '${env.dockerLogin}' 
        dockerImageName = registry+":"+${env.BUILD_ID}

    }

    agent any 

    stages { 

        stage('Cloning our Git') { 

            steps { 

                git '${env.gitUrl}' 

            }

        } 
        stage('Building our image') { 

            steps { 

                script { 

                    dockerImage = docker.build "${env.dockerImageName}"

                }

            } 

        }

        stage('Deploy our image') { 

            steps { 

                script { 

                    docker.withRegistry( '', "${env.registryCredential}" ){
                        dockerImage.push() 
                    }

                } 

            }

        } 

        stage('Cleaning up') { 

            steps { 

                sh "docker rmi $registry:$BUILD_NUMBER" 

            }

        } 

    }

}