pipeline {
    agent none 

	stages {
        stage('Git Checkout dockerfile') { 
	agent{label 'label3'}
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/apurva1j/UCDPipeline.git']]])
            }
        }

		stage('Build docker image'){
			agent{label 'lable3'}
			steps{
				script{
				docker.build("/home/apurva/tmp/poc/workspace/POCUCDPipeline")
				}
			}
		}
	

    }
}
