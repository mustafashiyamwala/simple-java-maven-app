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
	}
}