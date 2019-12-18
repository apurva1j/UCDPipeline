pipeline {
    agent none 

	stages {
        stage('Git Checkout dockerfile') { 
	agent{label 'label2'}
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/apurva1j/UCDPipeline.git']]])
            }
        }


	

    }
}
