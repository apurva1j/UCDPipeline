pipeline {
    agent any 
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
		
        stage('Deploy') { 
            steps {
                bat "echo Deploy"
            }
        }
    }
}
