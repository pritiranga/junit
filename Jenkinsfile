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
                emailext attachmentsPattern: 'target/surefire-reports', body: '', subject: 'Status of pipeline: ${currentBuild.fullDisplayName}', to: 'priti.ranga@testingxperts.com'
            }
        }
    }
       
   
   
