pipeline {
    agent any 
 	environment
	{
	ant_build = "C:\\Apurva\\JenkinsWorkspace\\ant1\\build.xml"
	}
	stages {
        stage('Git Checkout') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/apurva1j/POC1.git']]])
            }
        }
        stage('Test') { 
            steps {
                bat "echo Test"
            }
        }
	 stage('Sonarqube') {
		environment {
        scannerHome = tool 'SonarScannerLocal'
		}
		steps {
        withSonarQubeEnv('SonarLocal') {
            bat "${scannerHome}/bin/sonar-scanner"
        }
		}
		}
		stage('Build') {
		steps
		{
		withAnt(installation: 'Ant 1.10.7', jdk: 'jdk-11.0.4') {
		// some block
		bat "ant -f ${ant_build}"
		}
}
		}		
        stage('Deploy') { 
            steps {
                bat "echo Deploy"
            }
        }
    }
}
