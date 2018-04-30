@Library('hybris-geuk@v1.6') _ // Load Required libraries from Shared Pipeline Library

pipeline {
    agent any
    stages{
        stage('Dummy'){
            steps{
                echo "Dummy"
            }
        }
    }
    post {
      success {
            env.WORKDIR_SPACE=""
    		sendSlackNotification type: 'build-succeed'
    	}
    	unstable {
    		sendSlackNotification type: 'build-unstable'
    	}
    	failure {
    		sendSlackNotification type: 'build-failed'
    	}
    	aborted {
    		sendSlackNotification type: 'build-aborted'
    	}
    }
}
