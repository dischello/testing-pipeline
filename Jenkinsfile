/*
pipeline {
    agent any
    stages{
        stage('checkout'){
            steps{
                checkout scm
            }
        }
    }
}
*/
node('master'){
    stage('Checkout'){
        checkout([
            $class: 'GitSCM', 
            branches: scm.branches, 
            doGenerateSubmoduleConfigurations: scm.doGenerateSubmoduleConfigurations,
            extensions: scm.extensions + [[$class: 'CheckoutOption', timeout: 120]],
            userRemoteConfigs: scm.userRemoteConfigs
            ])
    }
}
