@Library('hybris-geuk@v1.6') _ // Load Required libraries from Shared Pipeline Library

pipeline {
    agent any
    stages{
        stage('Dummy'){
            steps{
                script{
                    env.HYBRIS_TESTS="SoapUI,QA_API_Tests"}
                sendSlackNotification type: 'build-started'
    		sendSlackNotification type: 'build-succeed'
                echo "${env.HYBRIS_TESTS}"
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
