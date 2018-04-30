@Library('hybris-geuk@bugfix/test-slack-notification-lib') _ // Load Required libraries from Shared Pipeline Library

pipeline {
    agent any
    stages{
        stage('Dummy'){
            steps{
                script{
                    env.HYBRIS_TESTS="SoapUI,QA_API_Tests"
                    echo "${env.WORKSPACE}"
                    env.WORKDIR_SPACE="${env.WORKSPACE}"
                    env.ARTIFACT_VERSION="release-6.0.1"
                    def failedTests = "Anonymous and user's carts should be merged on login.03.05.01 - Both Anonymous and Logged in carts are from the US, Anonymous cart is removed after merge, products are in User's cart"
                }
                sendSlackNotification type: 'build-started'
    		sendSlackNotification type: 'build-unstable'
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
