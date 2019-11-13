pipeline {
    agent any 
 	environment
	{
	ant_build = "C:\\Apurva\\JenkinsWorkspace\\ant2\\build.xml"
	}
	stages {
        stage('Git Checkout') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/apurva1j/POC2.git']]])
            }
        }

		stage('Build') {
		steps
		{
		withAnt(installation: 'Ant 1.10.7', jdk: 'jdk-11.0.4') {
		bat "ant -f ${ant_build}"
		}
}
		}
		
	stage('upload') {
           steps {
              script { 
                 def server = Artifactory.server 'frogArtifactory'
                 def uploadSpec = """{
                    "files": [{
                       "pattern": "C:/Apurva/Bars/",
                       "target": "SampleRepo"
                    }]
                 }"""

                 server.upload(uploadSpec) 
               }
            }
        }


	stage('Artifactory download') {
	steps {		
	script {
			def server = Artifactory.server 'frogArtifactory'
			def downloadSpec = """{
			"files": [
			{
				"pattern": "SampleRepo/*.bar",
				"target": "C:/Apurva/ArtifactoryDl/"
			}]
			}"""
	//server.download(downloadSpec)
	server.download spec: downloadSpec
	}
	}
	}
	

    }
}
