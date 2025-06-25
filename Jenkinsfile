pipeline {
	agent any
	environment {
		DOCKER_IMAGE = 'hello-world-python:latest' //Docker Image Name
	}
	
	stages {
		stage('Checkout') {
			steps {
				git branch: 'main',
				url:'https://github.com/sachink786/jenkins_docker_python_hello_world.git'
					}
				}
		stage('Docker Build'){
			steps {
				script{
					//check if docker file exists
					if (fileExists('Dockerfile')){
						sh "docker build -t ${env.DOCKER_IMAGE} ."
					} else {
						error "Dockerfile not fount. please create one for pytho app"
						}
					}
				}
			}
		stage('Docker Run '){
			steps{
				sh "docker run --rm ${env.DOCKER_IMAGE}"
				}
			}
		}
	post {
			success {
				echo 'Python application Docker image built successfully.'
			}
			failure{
				echo 'Docker build or run failed.'
			}
		}
	}

				
