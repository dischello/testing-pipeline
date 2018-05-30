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
	    agent {lable {'master'}}
            steps{
	    	stash include: '/var/lib/jenkins/workspace/test_pipeline_checkout_and_github_poll/*', name: 'Git_Revision'
		unstash 'Git_Revision'
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
