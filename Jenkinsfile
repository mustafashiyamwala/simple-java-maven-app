pipeline{
	agent any
	
	stages{
		stage('Pull'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/mustafashiyamwala/simple-java-maven-app.git']]])
							
			}
		}
		stage('Build'){
			steps{
				sh 'mvn -B -DskipTests clean package'
				archiveArtifacts artifacts: 'target/*.jar', fingerprint: true			
			}
		}
		stage('Test'){
			steps{
				sh 'mvn test'			
			}
			
			post{
				always{
					junit 'target/surefire-reports/*.xml'
				}
			}
		}
		stage('Deploy'){
			steps{
				sh echo After Deployment ${currentBuild.result}			
			}
		}
	}
	post{
		success{
			mail bcc: '', body: 'Thanks', cc: '', from: '', replyTo: '', subject: 'Success', to: 'mustafashiyamwala786@gmail.com'
		}
		failure{
			mail bcc: '', body: 'Thanks', cc: '', from: '', replyTo: '', subject: 'Failure', to: 'mustafashiyamwala786@gmail.com'
		}
	}	
}