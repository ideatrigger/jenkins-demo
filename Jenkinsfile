pipeline {
	environment {
	  //enables caching of maven repos between builds
	  JAVA_TOOL_OPTIONS = '-Duser.home=/root'
	}
    agent {
		docker {
		    image 'ryerson/cfs-admin-jenkins-stage-runner'
		    args '-v /root/.m2:/root/.m2 -v /var/run/docker.sock:/var/run/docker.sock'
		   	registryUrl 'https://ai-registry.prodint.ryerson.ca'
		    alwaysPull	true
		}
    }

	stages {
		stage("Compile") {
			steps {
				sh "mvn clean compile"
			}
		}
		
		stage("Unit Test") {
			steps {
				sh "mvn test"
			}
		}
	}
}