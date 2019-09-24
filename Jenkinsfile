pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/apurva1j/sample1.git']]])
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
        withSonarQubeEnv('SonalLocal') {
            bat "${scannerHome}/bin/sonar-scanner"
        }
        timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
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