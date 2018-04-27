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
          env.WORKDIR_SPACE="."
    		sendSlackNotification type: 'build-succeed'
    	}
    	unstable {
            env.WORKDIR_SPACE="."
    		sendSlackNotification type: 'build-unstable'
    	}
    	failure {
            env.WORKDIR_SPACE="."
    		sendSlackNotification type: 'build-failed'
    	}
    	aborted {
            env.WORKDIR_SPACE="."
    		sendSlackNotification type: 'build-aborted'
    	}
    }
}

node('master'){
    stage('Checkout'){
        sendSlackNotification
    }
}
