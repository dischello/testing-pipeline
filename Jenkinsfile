@Library('hybris-geuk@v1.6') _ // Load Required libraries from Shared Pipeline Library

pipeline {
    agent any
    stages{
        stage('Dummy'){
            steps{
            env.HYBRIS_TESTS="SoapUI,QA_API_Tests"
    		sendSlackNotification type: 'build-succeed'
            }
        }
    }
    post {
      success {
            //env.HYBRIS_TESTS="SoapUI,QA_API_Tests"
    		//sendSlackNotification type: 'build-succeed'
    	}
    	unstable {
            //env.HYBRIS_TESTS="SoapUI,QA_API_Tests"
    		//sendSlackNotification type: 'build-unstable'
    	}
    	failure {
            //env.HYBRIS_TESTS="SoapUI,QA_API_Tests"
    		//sendSlackNotification type: 'build-failed'
    	}
    	aborted {
            //env.HYBRIS_TESTS="SoapUI,QA_API_Tests"
    		//sendSlackNotification type: 'build-aborted'
    	}
    }
}
