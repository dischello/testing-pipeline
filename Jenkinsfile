@Library('hybris-geuk@v1.6') _ // Load Required libraries from Shared Pipeline Library

pipeline {
    agent any
    options {
        skipDefaultCheckout() // Disable SCM checkout running for every stage
        disableConcurrentBuilds() // Disable concurent builds
        buildDiscarder(logRotator(numToKeepStr:'5'))
    }
    stages{
        stage('Dummy'){
            steps{
	    sh 'mkdir test'
		    dir('./test'){
		    sh "git init"
		    sh "git remote add origin https://github.com/dischello/testing-pipeline"
		    sh "git config core.sparsecheckout true"
		    sh 'echo "gelscode/gelsecomm" >> .git/info/sparse-checkout'
		    sh 'echo "gelscode/config" >> .git/info/sparse-checkout'
			    
		    }
            checkout([
						            $class: 'GitSCM',
						            branches: scm.branches,
						            doGenerateSubmoduleConfigurations: scm.doGenerateSubmoduleConfigurations,
						            extensions: scm.extensions + [[$class: 'CheckoutOption', timeout: 30]] + [[$class: 'CloneOption', depth: 2, shallow: true, timeout: 30]],
						            userRemoteConfigs: scm.userRemoteConfigs
						            ])
            }
        }
    }
    post {
      success {
          echo "Success"
            //env.HYBRIS_TESTS="SoapUI,QA_API_Tests"
    		//sendSlackNotification type: 'build-succeed'
    	}
    	unstable {
            echo "Unstable"
            //env.HYBRIS_TESTS="SoapUI,QA_API_Tests"
    		//sendSlackNotification type: 'build-unstable'
    	}
    	failure {
            echo "Failed"
            //env.HYBRIS_TESTS="SoapUI,QA_API_Tests"
    		//sendSlackNotification type: 'build-failed'
    	}
    	aborted {
            echo "Aborted"
            //env.HYBRIS_TESTS="SoapUI,QA_API_Tests"
    		//sendSlackNotification type: 'build-aborted'
    	}
    }
}
