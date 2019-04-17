pipeline{
	agent any
	
	stages{
		stage('Build'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/mustafashiyamwala/simple-java-maven-app.git']]])
				
			
			}
		}
	}
}