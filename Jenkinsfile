pipeline{

	agent any

		stages{

			stage('Checkout'){

					steps{

						git branch: "main", url: 'https://github.com/Nikhitha0402/g1-allergy-service.git'

						}

					}

			stage('Build'){

					steps{

						sh 'chmod a+x mvnw'

						sh './mvnw clean package -DskipTests=true'

						}

					post{

						always{

							archiveArtifacts 'target/*.jar'

							}

						}

				}

			stage('DockerBuild') {

						steps {

							sh 'docker build -t nikhitha0402/allergy-service:latest .'

							}

						}

			stage('Login') {

					steps {

						sh 'echo Nikhitha@9531 | docker login -u nikhitha0402  --password-stdin'

						}

					}

			stage('Push') {

					steps {

						sh 'docker push nikhitha0402/allergy-service'

						}
	
					}
				}

		post {

			always {

				sh 'docker logout'

				}

			}

}
