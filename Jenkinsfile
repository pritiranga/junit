    pipeline {
        agent any
        tools {
            maven 'Maven'
        }

        stages {
            stage('Build and Test') {
                steps {
                    // for build
                    sh "mvn -Dmaven.test.failure.ignore=true clean compile test"
                    // for unit testing
                    junit(testResults: 'target/surefire-reports/*.xml', allowEmptyResults : true, skipPublishingChecks: true)
                }
            }
        }
        post {
            always {
                emailext attachLog: true, body: '${FILE,path=\'target/surefire-reports\'}', subject: 'Status of pipeline', to: 'priti.ranga@testingxperts.com'
        }
    }
    }
   
   
